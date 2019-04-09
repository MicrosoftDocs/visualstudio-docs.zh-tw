---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保護, community edition, obfuscation, .NET, 免費, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: 了解如何使用 Visual Studio 中免費的 Dotfuscator Community 保護您的 .NET 應用程式。
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bf77f2796a224d6fad81c4a1485ba82f8822cfcc
ms.sourcegitcommit: 40393347a36779230d128f2355a911632a8d458e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58866701"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***PreEmptive Protection - Dotfuscator*** 可為 .NET 應用程式提供全方位的保護，而且很容易就能夠整合到您的軟體開發生命週期中。
使用它來強化、保護及清理傳統型、行動裝置、伺服器和嵌入式應用程式，以協助保護商業機密和其他智慧財產 (IP)、減少盜版和仿冒，並防止竄改及未經授權的偵錯。
Dotfuscator 不需要其他程式設計作業，甚至不需要存取原始程式碼，就可以在編譯的組件上執行。

![PreEmptive Protection - Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>為何保護很重要

保護您的「智慧財產」(IP) 非常重要。
您的應用程式程式碼包含可視為智慧財產的設計和實作詳細資料。
不過，以 .NET Framework 為基礎建置的應用程式[包含大量中繼資料與高層級中繼程式碼][assemblies]，可以透過任一種免費的自動化工具，輕鬆地對應用程式進行還原工程。
藉由中斷並阻止還原工程，您可以防止未經授權的智慧財產公開，並展示您的程式碼包含商業機密。
Dotfuscator 可以[混淆][obfuscation]您的 .NET 組件來阻礙還原工程，並仍維持應用程式原有的行為。

「保護應用程式的完整性」也相當重要。
除了還原工程之外，惡意執行者也可能嘗試製作盜版應用程式、改變應用程式在執行階段的行為，或是操控資料。
Dotfuscator 可以在您的應用程式中插入[偵測及回應未經授權之使用者][checks]的功能，包括竄改、第三方偵錯與已破解 (Root) 的裝置。

如需 Dotfuscator 如何整合到安全軟體開發週期的詳細資訊，請參閱 PreEmptive Solutions 的 [SDL 應用程式保護頁面][sdl-protection]。

## <a name="about-dotfuscator-community"></a>關於 Dotfuscator Community

您的 Microsoft Visual Studio 包含一份 ***PreEmptive Protection - Dotfuscator Community***，可免費供個人使用。
(這個免費版本先前稱為 Dotfuscator Community Edition 或 Dotfuscator CE。)如需安裝隨附於 Visual Studio 的 Dotfuscator Community 版本的詳細資訊，請參閱[安裝頁面][install]。

Dotfuscator Community 針對開發人員、架構設計人員和測試人員提供多種[軟體保護及強化][software-protection]服務。
Dotfuscator Community 中包含的 [.NET Obfuscation][obfuscation] 及其他[應用程式保護][app-protection]功能的範例為：

* *[重新命名][renaming]* 識別項，使對編譯過的組件進行還原工程更困難。
* *[反竄改][tamper]* 會偵測遭竄改應用程式的執行，以及終止或回應遭竄改的工作階段。
* *[反偵錯][debug]* 會偵測附加以執行應用程式的偵錯工具，以及終止或回應受偵錯的工作階段。
* *[防裝置破解][root]* 可偵測應用程式是否正在已被破解的 Android 裝置上執行，然後在這些裝置上終止或回應工作階段。
* *[應用程式到期行為][shelflife]*，它會編碼「生命結束」日期並終止已到期的應用程式工作階段。

如需這些功能的詳細資料，包括如何將它們整合到您的應用程式保護策略，請參閱[功能頁面][capabilities]。

Dotfuscator Community 提供現成的基本保護。
註冊的 Dotfuscator Community 的使用者，以及 ***PreEmptive Protection - Dotfuscator*** Professional (全球最先進的 [.NET Obfuscator][net-obfuscator]) 使用者，將能取得更多保護方法。
如需增強 Dotfuscator 的相關資訊，請參閱[升級頁面][upgrades]。

## <a name="getting-started"></a>使用者入門

::: moniker range="vs-2019"

若要開始從 Visual Studio 使用 Dotfuscator Community，請在 [搜尋方塊] \(Ctrl+Q) 中輸入 `dotfuscator`。

* 如果您已安裝 Dotfuscator Community，[搜尋方塊]會在 [功能表] 標題下，顯示啟動 Dotfuscator Community 的選項。 如需詳細資訊，請參閱[完整 Dotfuscator Community 使用者指南的使用者入門頁面][get-started]。
* 如果尚未安裝 Dotfuscator Community，[搜尋方塊] 會改為在 [個別元件] 標題下顯示 [安裝 PreEmptive Protection - Dotfuscator]。 如需詳細資訊，請參閱[安裝頁面][install]。

::: moniker-end

::: moniker range="vs-2017"

若要開始從 Visual Studio 使用 Dotfuscator Community，請在 [快速啟動] \(Ctrl+Q) 搜尋列中輸入 `dotfuscator`。

* 如果已經安裝 Dotfuscator Community，[快速啟動] 將會顯示啟動 Dotfuscator Community 使用者介面的 [功能表] 選項。 如需詳細資訊，請參閱[完整 Dotfuscator Community 使用者指南的使用者入門頁面][get-started]。
* 如果您尚未安裝 Dotfuscator Community，[快速啟動] 將會顯示相關的 [安裝] 選項。 如需詳細資訊，請參閱[安裝頁面][install]。

::: moniker-end

您也可以從 [preemptive.com 上的 Dotfuscator 下載頁面][download]取得**最新版本**的 Dotfuscator Community。

## <a name="full-documentation"></a>完整文件

本頁面及其子頁面提供 Dotfuscator Community 功能的高階概觀，以及[安裝該工具的指示][install]。

如需詳細的使用指示，請參閱 [preemptive.com 上的完整 Dotfuscator Community 使用者指南][full]，其中包含[如何開始使用 Dotfuscator Community 使用者介面][get-started]。

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html
