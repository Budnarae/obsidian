---
tags:
  - directX11
  - translation
---
![[642bb0483c2868b445df8e624a08af19_MD5.jpeg]]

# Summary

In the previous tutorials, the world looks boring because all the objects are lit in the same way.

이전 튜토리얼에서, 이전 월드는 모든 물체가 똑같이 밝혀지기 때문에 지루해보였다.

This tutorial will introduce the concept of simple lighting and how it can be applied.

이 튜토리얼에서는 간단한 조명의 개념과 이를 적용하는 방법을 소개한다.

The technique used will be lambertian lighting.

이 기술은 램버시안 조명 개념을 사용한다.

The outcome of this tutorial will modify the previous example to include a light source.

이번 튜토

This light source will be attached to the cube in orbit. The effects of the light can be seen on the center cube.

# Source

(SDK root)\Samples\C++\Direct3D11\Tutorials\Tutorial06

# Lighting

In this tutorial, the most basic type of lighting will be introduced: lambertian lighting. Lambertian lighting has uniform intensity irrespective of the distance away from the light. When the light hits the surface, the amount of light reflected is calculated by the angle of incidence the light has on the surface. When a light is shined directly on a surface, it is shown to reflect all the light back, with maximum intensity. However, as the angle of the light is increased, the intensity of the light will fade away.

To calculate the intensity that a light has on a surface, the angle between the light direction and the normal of the surface has to be calculated. The normal for a surface is defined as a vector that is perpendicular to the surface. The calculation of the angle can be done with a simple dot product, which will return the projection of the light direction vector onto the normal. The wider the angle, the smaller the projection will be. Thus, this gives us the correct function to modulate the diffused light with.

![[4353e841252db1deef3dd9f47b0c3c3a_MD5.jpeg]]

The light source used in this tutorial is an approximation of directional lighting. The vector which describes the light source determines the direction of the light. Since it's an approximation, no matter where an object is, the direction in which the light shines towards it is the same. An example of this light source is the sun. The sun is always seen to be shining in the same direction for all objects in a scene. In addition, the intensity of the light on individual objects is not taken into consideration.

Other types of light include point lights, which radiate uniform light from their centers, and spot lights, which are directional but not uniform across all objects.

# Initializing the Lights

In this tutorial, there will be two light sources. One will be statically placed above and behind the cube, and another one will be orbiting the center cube. Note that the orbiting cube in the previous tutorial has been replaced with this light source.

Since lighting is computed by the shaders, the variables would have to be declared and then bound to the variables within the technique. In this sample, we just require the direction of the light source, as well as its color value. The first light is grey and not moving, while the second one is an orbiting red light.

      
    // Setup our lighting parameters
    XMFLOAT4 vLightDirs[2] =
    {
        XMFLOAT4( -0.577f, 0.577f, -0.577f, 1.0f ),
        XMFLOAT4( 0.0f, 0.0f, -1.0f, 1.0f ),
    };
    XMFLOAT4 vLightColors[2] =
    {
        XMFLOAT4( 0.5f, 0.5f, 0.5f, 1.0f ),
        XMFLOAT4( 0.5f, 0.0f, 0.0f, 1.0f )
    };

The orbiting light is rotated just like the cube in the last tutorial. The rotation matrix applied will change the direction of the light, to show the effect that it is always shining towards the center. Note that function **XMVector3Transform** is used to multiply a matrix with a vector. In the previous tutorial, we multiplied just the transformation matrices into the world matrix, then passed into the shader for transformation. However, for simplicity's sake in this case, we're actually doing the world transform of the light in the CPU.

      
    // Rotate the second light around the origin
    XMMATRIX mRotate = XMMatrixRotationY( -2.0f * t );
    XMVECTOR vLightDir = XMLoadFloat4( &vLightDirs[1] );
    vLightDir = XMVector3Transform( vLightDir, mRotate );
    XMStoreFloat4( &vLightDirs[1], vLightDir );

The lights' direction and color are both passed into the shader just like the matrices. The associated variable is called to set, and the parameter is passed in.

      
    //
    // Update matrix variables and lighting variables
    //
    ConstantBuffer cb1;
    cb1.mWorld = XMMatrixTranspose( g_World );
    cb1.mView = XMMatrixTranspose( g_View );
    cb1.mProjection = XMMatrixTranspose( g_Projection );
    cb1.vLightDir[0] = vLightDirs[0];
    cb1.vLightDir[1] = vLightDirs[1];
    cb1.vLightColor[0] = vLightColors[0];
    cb1.vLightColor[1] = vLightColors[1];
    cb1.vOutputColor = XMFLOAT4(0, 0, 0, 0);
    g_pImmediateContext->UpdateSubresource( g_pConstantBuffer, 0, NULL, &cb1, 0, 0 );

# Rendering the Lights in the Pixel Shader

Once we have all the data set up and the shader properly fed with data, we can compute the lambertian lighting term on each pixel from the light sources. We'll be using the dot product rule discussed previously.

Once we've taken the dot product of the light versus the normal, it can then be multiplied with the color of the light to calculate the effect of that light. That value is passed through the saturate function, which converts the range to [0, 1]. Finally, the results from the two separate lights are summed together to create the final pixel color.

Consider that the material of the surface itself is not factored into this light calculation. The final color of the surface is a result of the light's colors.

      
    //
    // Pixel Shader
    //
    float4 PS( PS_INPUT input) : SV_Target
    {
        float4 finalColor = 0;
        
        //do NdotL lighting for 2 lights
        for(int i=0; i<2; i++)
        {
            finalColor += saturate( dot( (float3)vLightDir[i],input.Norm) * vLightColor[i] );
        }
        return finalColor;
    }

Once through the pixel shader, the pixels will be modulated by the lights, and you can see the effect of each light on the cube surface. Note that the light in this case looks flat because pixels on the same surface will have the same normal. Diffuse is a very simple and easy lighting model to compute. You can use more complex lighting models to achieve richer and more realistic materials.
