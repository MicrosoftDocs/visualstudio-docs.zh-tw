---
title: "升級 Dotfuscator Community Edition (CE) | Microsoft Docs"
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 保護, Community Edition, 混淆, .NET, 免費, Visual Studio 2017, 升級, 命令列"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
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
description: "了解如何升級 Visual Studio 2017 中隨附的免費 Dotfuscator Community Edition。"
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
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
ms.openlocfilehash: 60ca38639f6523cdbace4efa4aa48b48d5e9a886
ms.contentlocale: zh-tw
ms.lasthandoff: 06/23/2017

---

# 升級 Dotfuscator Community Edition (CE)
<a id="upgrade-dotfuscator-community-edition-ce" class="xliff"></a>

Dotfuscator Community Edition (Dotfuscator CE) 為所有使用 Microsoft Visual Studio 的開發人員立即提供許多應用程式保護與強化功能。
不過，使用者在升級其 Dotfuscator 版本之後，會有更多功能可用。

## 註冊 Dotfuscator CE
<a id="registering-dotfuscator-ce" class="xliff"></a>

Dotfuscator CE 的已註冊使用者可存取額外的功能，例如[命令列支援][cli]，這可讓您輕鬆地將 Dotfuscator CE 整合到自動建置流程。

註冊不但簡單快速，而且完全免費。
若要註冊 Dotfuscator CE，請參閱[完整《Dotfuscator CE User Guide》(Dotfuscator CE 使用者指南) 之 ＜Getting Started＞(使用者入門) 頁面上的＜Registering Dotfuscator CE＞ (註冊 Dotfuscator CE) 一節][register-ce]。

## Dotfuscator Professional
<a id="dotfuscator-professional" class="xliff"></a>

Dotfuscator Community Edition 提供基本層級的保護，而 **_PreEmptive Protection - Dotfuscator_ Professional Edition** 則包含增強的混淆轉換和保護功能。
它們包括：

* 智慧財產權保護
  * 額外的重新命名選項，包括 Enhanced Overload Induction™ 和隨機化識別碼選取。
  * 用於解碼經過混淆處理之堆疊追蹤的工具。
  * 存取企業級混淆轉換，包括[目標為防止自動程式碼反向組譯的轉換][control-flow]。
  * 能夠[混淆敏感性字串][string-encryption]，以防止執行反向組譯程式碼的簡單搜尋。
  * 能夠[以不顯眼的方式將擁有權和發佈字串嵌入您的組件][watermarking] (軟體浮水印)，讓您判斷未經授權的軟體漏洞來源。
  * 能夠[將多個組件合併成一個組件][linking]，由於消除了關注點分離 (Separation of Concerns) 的問題，因此攻擊者更難判斷程式碼項目的角色。
  * 能夠[自動從您的應用程式移除未使用的程式碼][pruning]，以減少送出的敏感性程式碼數量。
* 應用程式完整性保護
  * 額外的[應用程式防禦行為][check-actions]。
  * 能夠將反竄改和反偵錯程式碼插入 `.dll` 組件。
  * 能夠在應用程式生命週期結束期限之前提供一段警告期間。
  * 能夠在生命週期結束警告期間或在期限之後通知應用程式程式碼。
  * 遙測加密。
* 應用程式監視
  * 能夠收集和儲存在暫時性網路中斷期間收集到的資訊。
  * 能夠收集個人識別資訊。
  * 不限次數地使用[功能追蹤][features]。
  * 能夠追蹤您的程式碼所攔截和擲回的例外狀況，以及未處理的例外狀況。
  * 能夠追蹤 `.dll` 組件中的例外狀況。
  * 遙測加密。

Dotfuscator Professional 是業界標準 [.NET 混淆器][net-obfuscator]，適合需要持續支援、維護和產品更新的企業開發人員。
此外，Dotfuscator Professional 提供與 Visual Studio 的緊密整合，並針對商業用途授權。

如需 Dotfuscator Professional 之進階應用程式保護功能的詳細資訊，請前往 PreEmptive Solutions 的 [Dotfuscator 概觀頁面][product-about]並[與 Community Edition 進行比較][product-compare]。
[您可以在 preemptive.com 要求取得完整支援的試用版][eval]。

## 另請參閱
<a id="see-also" class="xliff"></a>

[完整《Dotfuscator CE User Guide》(Dotfuscator CE 使用者指南) 中的本主題][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Check%20Actions.html
[features]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Feature_Usage_Tracking_and_the_Feature_Attribute.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html

