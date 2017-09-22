---
title: "Dotfuscator 的功能 | Microsoft Docs"
ms.date: 2017-06-22
ms.devlang: dotnet
ms.technology:
- vs-ide-general
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保護, Community Edition, 混淆, .NET, 免費, Visual Studio 2017"
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: "了解 Visual Studio 2017 中隨附之免費 Dotfuscator Community Edition 的功能。"
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 9193020b9031b5e1a5637fd4ec207d0449ec85ae
ms.contentlocale: zh-tw
ms.lasthandoff: 06/23/2017

---

# <a name="capabilities-of-dotfuscator"></a>Dotfuscator 的功能

本頁的重點在於描述 Dotfuscator Community Edition (Dotfuscator CE) 的功能，並提供可透過[升級][upgrades]使用之進階選項的一些參考資訊。

Dotfuscator 是 .NET 應用程式的「建置後」系統。
透過 Dotfuscator CE，Visual Studio 使用者可以[混淆組件][obfuscation]，並將[主動防禦][checks]和[分析追蹤][analytics]插入應用程式，Dotfuscator 完全不需要存取原始程式碼。
Dotfuscator 採用多種方法來保護您的應用程式，並建立多層保護策略。

Dotfuscator CE 支援各種 .NET 組件和應用程式類型，包括[通用 Windows 平台 (UWP)][uwp] 和 [Xamarin][xamarin]。

## <a name="intellectual-property-protection"></a>智慧財產權保護

應用程式的設計、行為和實作都屬於智慧財產權 (IP)。
不過，針對 .NET Framework 建立的應用程式基本上一目暸然；[因為 .NET 組件包含高階中繼資料和中繼程式碼][assemblies]，所以可輕易對這些組件進行還原工程。

Dotfuscator CE 包含[重新命名][renaming]形式的基本 [.NET 混淆化][obfuscation]。
使用 Dotfuscator 混淆您的程式碼，可降低未經授權就透過還原工程存取原始程式碼的風險，因為重要的命名資訊不再公開。
混淆也彰顯您保護程式碼以防遭到探查的努力，這項重要的步驟可確保您的 IP 會當作營業祕密受到合法保護。

Dotfuscator CE 的許多[應用程式完整性保護功能](#application-integrity-protection)可進一步防止還原工程。
例如，居心叵測的執行者可能會嘗試將偵錯工具附加至您正在執行的應用程式執行個體，以了解程式邏輯。
Dotfuscator 可將[反偵錯行為][debug]插入您的應用程式，對此進行混淆。

## <a name="application-integrity-protection"></a>應用程式完整性保護

除了保護您的原始程式碼，確保您的應用程式依照設計使用也很重要。
攻擊者可能會嘗試劫持您的應用程式以規避授權原則 (亦即軟體盜用)、竊取或竄改應用程式所處理的敏感性資料，或是變更應用程式的行為。

Dotfuscator CE 可將[應用程式驗證程式碼][checks]插入您的組件，包括[反竄改][tamper]和[反偵錯][debug]措施。
如果偵測到無效的應用程式狀態，驗證程式碼可[要求應用程式程式碼適當地解決此情況][check-app]。
或者，如果您不想要撰寫程式碼來處理應用程式使用不當的情況，Dotfuscator 也可以插入[遙測報告][check-telemetry]和[回應][check-action]行為，而不需要對您的原始程式碼進行任何修改。

許多相同的方法也可用來強制執行評估或試用版軟體的[生命週期結束期限][shelflife]。

## <a name="application-monitoring"></a>應用程式監視

開發應用程式時，請務必了解使用者的行為模式，包括搶鮮版 (Beta) 測試人員和舊版使用者。
應用程式分析可讓您追蹤應用程式的使用頻率及使用情況，包括客戶體驗到哪些錯誤。

Dotfuscator CE 可將[例外狀況追蹤][exceptions]、[工作階段追蹤][sessions]和[功能追蹤][features]程式碼插入您的應用程式。
此處理過的應用程式會在執行時，將分析資料傳輸至所設定的 [PreEmptive Analytics 端點][endpoints]。

## <a name="see-also"></a>另請參閱

[完整《Dotfuscator CE User Guide》(Dotfuscator CE 使用者指南) 中的本主題][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[assemblies]: https://docs.microsoft.com/en-us/dotnet/standard/assembly-format
[uwp]: https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]: https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]: upgrades.md

[obfuscation]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]: https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[analytics]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_overview.html
[endpoints]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_overview.html#endpoints

[checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[shelflife]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html
[exceptions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_exceptions.html
[sessions]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_sessions.html
[features]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_features.html
[check-telemetry]: https://www.preemptive.com/dotfuscator/ce/docs/help/analytics_checks.html

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html

