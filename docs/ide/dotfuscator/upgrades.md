---
title: 升級 Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保護, community edition, obfuscation, .NET, 免費, Visual Studio 2019, Visual Studio 2017, Visual Studio, 升級, 命令列
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: 了解如何升級 Visual Studio 中隨附的免費 Dotfuscator Community。
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 78a26da7734e4fa74a9b312b41786caca4b7cc67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652815"
---
# <a name="upgrade-dotfuscator-community"></a>升級 Dotfuscator Community

Dotfuscator Community 為所有使用 Microsoft Visual Studio 的開發人員立即提供許多應用程式保護與強化功能。
不過，使用者在升級其 Dotfuscator 版本之後，會有更多功能可用。

## <a name="registering-dotfuscator-community"></a>註冊 Dotfuscator Community

Dotfuscator 社區的已註冊使用者可存取額外的功能，例如[命令列支援][cli]，這可讓您輕鬆地將 Dotfuscator 的社區整合到您的自動化組建流程中。 註冊也會授與內建工具的存取權，用來[解碼模糊堆疊追蹤][decode-obfuscated]。

註冊不但簡單快速，而且完全免費。
若要註冊 Dotfuscator 的社區，請參閱[完整的 Dotfuscator 社區使用者指南中的指示][register-ce]。

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Dotfuscator Community 提供基本層級的保護，而 ***PreEmptive Protection - Dotfuscator Professional***  則包含增強的混淆轉換和保護功能，例如：

* 智慧財產權保護
  * 額外的重新命名選項，包括 Enhanced Overload Induction™ 和隨機化識別碼選取。
  * 存取企業層級的混淆轉換，包括以[達到監控自動化程式碼 decompilation 為目標的轉換][control-flow]。
  * 能夠[隱藏機密字串][string-encryption]，讓反向組譯程式碼不可能簡單地搜尋。
  * [不顯眼方式將擁有權和散發字串內嵌至元件][watermarking]的能力，可讓您判斷未經授權的軟體洩漏來源。
  * 將[多個元件結合成一個][linking]的功能，讓攻擊者更難判斷程式碼專案的角色，因為已排除問題的分離。
  * 能夠[自動從您的應用程式移除未使用的程式碼][pruning]，以減少出貨的機密程式碼數量。
* 應用程式完整性保護
  * 其他[應用程式防護行為][check-actions]。
  * 能夠在應用程式生命週期結束期限之前提供一段警告期間。
  * 能夠在生命週期結束警告期間或在期限之後通知應用程式程式碼。

Dotfuscator Professional 是業界標準的[.Net 混淆][net-obfuscator]程式，適用于需要持續支援、維護和產品更新的企業開發人員。
此外，Dotfuscator Professional 提供與 Visual Studio 的緊密整合，並針對商業用途授權。

如需 Dotfuscator Professional 的先進應用程式保護功能的詳細資訊，請造訪先占式解決方案的[Dotfuscator 總覽頁面][product-about]，並[將其與 Dotfuscator 社區進行比較][product-compare]。
如有[完整支援的試用][eval]版，請 preemptive.com。

## <a name="see-also"></a>請參閱

[完整 Dotfuscator 社區使用者指南中的這篇文章][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html