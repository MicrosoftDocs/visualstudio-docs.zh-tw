---
title: Dotfuscator 的功能
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保護, community edition, obfuscation, .NET, 免費, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: 了解 Visual Studio 2017 中隨附的免費 Dotfuscator Community 功能。
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a36aa17207affa257cdbb2caec0f2d6d9392285b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590003"
---
# <a name="capabilities-of-dotfuscator"></a>Dotfuscator 的功能

本頁著重于 Dotfuscator 社區的功能，其中包含一些可透過[升級][upgrades]取得之 advanced 選項的參考。

Dotfuscator Community 是 .NET 應用程式的「建置後」系統。
有了它，Visual Studio 使用者就能夠[模糊處理元件][obfuscation]，並將[主動防禦措施][checks]插入應用程式中，而不需要 Dotfuscator 存取原始原始程式碼。
Dotfuscator 採用多種方法來保護您的應用程式，並建立多層保護策略。

Dotfuscator 的社區支援各種 .NET 元件和應用程式類型，包括[通用 Windows 平臺（UWP）][uwp]和[Xamarin][xamarin]。

## <a name="intellectual-property-protection"></a>智慧財產權保護

應用程式的設計、行為和實作都屬於智慧財產權 (IP)。
不過，針對 .NET 所建立的應用程式基本上是開放書籍;您可以輕鬆地對 .NET 元件進行還原工程，[因為它們包含高階的中繼資料和中繼程式碼][assemblies]。

Dotfuscator 社區包含重新[命名][renaming]形式的基本[.net 混淆][obfuscation]。
使用 Dotfuscator 混淆您的程式碼，可降低未經授權就透過還原工程存取原始程式碼的風險，因為重要的命名資訊不再公開。
混淆也彰顯您保護程式碼以防遭到探查的努力，這項重要的步驟可確保您的 IP 會當作營業祕密受到合法保護。

Dotfuscator Community 的許多[應用程式完整性保護功能](#application-integrity-protection)可進一步防止還原工程。
例如，居心叵測的執行者可能會嘗試將偵錯工具附加至您正在執行的應用程式執行個體，以了解程式邏輯。
Dotfuscator 可以將[反 debug 行為][debug]插入您的應用程式，以妨礙此動作。

## <a name="application-integrity-protection"></a>應用程式完整性保護

除了保護您的原始程式碼，確保您的應用程式依照設計使用也很重要。
攻擊者可能會嘗試劫持您的應用程式以規避授權原則 (也就是軟體盜用)、竊取或竄改應用程式所處理的敏感性資料，或是變更應用程式的行為。

Dotfuscator 的社區可以將[應用程式驗證程式代碼][checks]插入您的元件，包括[防篡改][tamper]、[反 debug][debug]和反 root 破解的[裝置][root]量值。
當偵測到不正確應用程式狀態時，驗證程式代碼可以[在應用程式程式碼上呼叫，以適當的方式處理情況][check-app]。
或者，如果您不想要撰寫程式碼來處理應用程式的無效用法，Dotfuscator 也可以插入[回應][check-action]行為，而不需要對您的原始程式碼進行任何修改。

其中許多相同的方法也可用來強制執行評估或試用版軟體的[生命週期結束期限][shelflife]。

## <a name="see-also"></a>請參閱

[完整《Dotfuscator Community 使用者指南》中的本主題][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
