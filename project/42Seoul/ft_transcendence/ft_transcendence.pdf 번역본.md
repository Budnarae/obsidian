
---

#42Seoul 

*Surprise*

---

Summary:
This project is about doing something you've never done before.
Remind yourself the beginning of your journey in computer science.
Look at you now. Time to shine!

Version: 15

요약:
이 프로젝트는 당신이 여태껏 한번도 해본 적 없는 것에 관한 것입니다.
당신이 컴퓨터 과학에 입문했던 당시를 돌아보세요.
그리고 지금의 당신을 보세요. 빛을 발할 때입니다!

버전: 15

---

Contents
목차

I Preamble
1 서두

II Essential Points
2 필수 포인트

III Mandatory part
3 기본 영역

IV Modules
4 모듈들

IV.1 Overview
개요

IV.2 Web
웹

IV.3 User Management
사용자 관리

IV.4 Gameplay and user experience
게임 플레이와 사용자 경험

IV.5 AI-Algo
인공지능 알고리즘

IV.6 Cybersecurity
보안

IV.7 Devops
데브옵스((소프트웨어 개발과 운영의 통합, 개발 단계에서부터 운영을 고려하여 두 영역의 담당자가 협업하는 것, development(개발)와 operation(운영)의 합성어))

IV.8 Gaming
게임

IV.9 Graphics
그래픽스

IV.10 Accessibility
접근성

IV.11 Server-Side Pong
서버 측의 Pong

V Bonus part
5 보너스 영역

VI Submission and peer-evaluation
6 제출과 동료 평가

---

# Chapter I. Preamble

(대충 핑퐁 게임을 하는 그림)

---

# Chapter II. Essential Points

This project is a complex undertaking, requiring decision-making within the specified constraints.  
이 프로젝트는 주어진 제약 내에서 의사결정을 요구하는 복잡한 작업입니다.

You have some flexibility in implementing certain modules, and it is left to your discretion within the scope of the subject.  
일부 모듈을 구현하는 데 있어서 유연성이 주어지며, 주제의 범위 내에서 본인의 재량으로 선택할 수 있습니다.

All your choices must be justifiable.  
모든 선택은 타당한 이유가 있어야 합니다.

If you believe it’s necessary to use nginx to set up your website, there’s no issue, but ask yourself first, is it truly necessary?  
nginx를 사용하여 웹사이트를 설정해야 할 필요성이 있다고 판단되면, 그 선택을 해도 괜찮습니다. 그러나 정말로 필요한지 먼저 생각해보세요.

Can I do without it?  
nginx 없이 해결할 방법이 있을지 고민해보세요.

Similarly, when faced with a library that could assist you, it’s crucial to understand whether it will fulfill your tasks.  
마찬가지로, 특정 라이브러리가 도움이 될 것 같을 때는 그 라이브러리가 실제로 요구하는 작업을 충족시킬 수 있는지 확실히 이해하는 것이 중요합니다.

You’re not expected to rework uninteresting sub-layers but rather to make the proposed features function.  
흥미롭지 않은 하위 작업을 재작업할 필요는 없으며, 제안된 기능이 정상적으로 동작하도록 만드는 것이 핵심입니다.

It’s crucial to understand that you’ll encounter decisions where doubts about implementing certain features will arise.  
의심이 드는 기능을 구현해야 할 때, 요구사항을 철저히 이해하는 것이 가장 중요합니다.

Initially, it is STRONGLY recommended to comprehend the project requirements thoroughly.  
처음에는 요구사항을 철저히 이해하는 것이 강력히 권장됩니다.

Once you’ve grasped what needs to be accomplished, it is necessary to stay within the framework of the project.  
요구되는 내용을 정확히 파악한 후, 프로젝트의 프레임워크 내에서 작업을 진행해야 합니다.

When we mention an imposed technology, it explicitly means that everything officially related to the requested framework/language is allowed.  
지정된 기술이 언급되었을 때, 그 기술과 공식적으로 관련된 모든 것만 사용해야 합니다.

However, we emphasize that when you wish to implement a module, all restrictions apply to that module.  
하지만 모듈을 구현할 때, 해당 모듈에 대한 제약이 적용된다는 점을 명심해야 합니다.

For instance, if you want to realize the project with the Backend module as specified in the subject, you can no longer use the default language and must adapt your project accordingly.  
예를 들어, 백엔드 모듈을 지정된 대로 구현하고 싶다면 기본 언어를 사용하지 않고 요청된 언어와 프레임워크를 맞춰야 합니다.

If you still want to create a backend using the default language, it’s also possible, but since you’re not using the requested language/framework, this module will not be considered valid.  
기본 언어를 사용해 백엔드를 구현하고 싶다면 그 방법도 가능하지만, 이 경우 해당 모듈은 유효하지 않게 됩니다.

Before concluding, it’s important to note that some modules intentionally have strong dependencies on others.  
마지막으로, 일부 모듈은 다른 모듈에 강한 의존성을 가질 수 있다는 점을 염두에 두어야 합니다.

Your choices are significant and must be justified during your evaluation.  
선택이 중요하며, 평가 과정에서 그 선택을 정당화해야 합니다.

Exercise caution.  
신중하게 결정하십시오.

Take the time to contemplate the design of your application with your choices before delving into the code – it’s crucial.  
코드를 작성하기 전에 애플리케이션 설계와 선택에 대해 충분히 고민하는 것이 중요합니다.

Have a fun! :)  
재미있게 작업하세요! :)

---

# Chapter III. Mandatory part

This project is about creating a website for the mighty Pong contest!
이 프로젝트의 목적은 터프한 퐁 대회를 즐길 수 있는 웹사이트를 만드는 것입니다!

> Caution
> 주의
> - The use of libraries or tools that provide an immediate complete solution for a global feature or a module is prohibited.
> - 과제 전체 혹은 모듈 전체의 기능을 즉시 그리고 통째로 제공하는 라이브러리 또는 도구의 사용은 금지됩니다.
> - Any direct instruction about the usage (can, must, can't) of a third party library or tool must be followed.
> - 서드 파티 라이브러리나 도구의 사용에 있어 직접적인 지시가 있으면(ex. 이렇게 해야 합니다, 이렇게 하지 말아야 합니다 등등) 무조건 해당 사항을 따라야 합니다.
> - During the evaluation, the team will justify any usage of library or tool that is not explicitly approved by the subject.
> - 과제에 직접적으로 명시되지 않은 라이브러리나 툴을 사용했다면 평가 때 그것을 왜 사용했는지 타당한 이유를 댈 수 있어야 합니다.
> - During the evaluation, the evaluator will take her/his responsibility and define if the usage of a specific library or tool is legit (and allowed) or almost solving an entire feature or module (and prohibited).
> - 평가를 하는 동안에, 평가자는 사용된 라이브러리나 도구가 적절하고 허용되었는지, 과제 혹은 모듈 전체에 대한 해결책을 제공하거나 사용이 금지되지는 않았는지 책임감을 가지고 평가하세요.

---

## III.1 Overview

Thanks to your website, users will play Pong with others. You have to provide a nice user interface and real-time multiplayer online games!
당신의 웹사이트 덕분에, 사용자들은 다른 사람들과 퐁 게임을 즐길 수 있을 것입니다. 당신은 훌륭한 사용자 인터페이스와 실시간 멀티플레이어 온라인 게임을 만들 수 있어야 합니다.

- Your project needs to adhere to the following guidelines as a minimum requirement, contributing only a small portion to the final grade.
- 

- The second part of this subject will offer additional modules that can replace or complete the following rules.
