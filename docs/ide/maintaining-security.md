---
title: 維護 Visual Studio 中的應用程式安全性 | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- unauthorized access
- Baseline Security Analyzer
- Microsoft Baseline Security Analyzer
- security [.NET Framework], best practices
- MBSA (Microsoft Baseline Security Analyzer)
- security [.NET Framework], maintaining after deployment
ms.assetid: 621d10c1-842b-4902-be60-bb9719591751
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f0594f7c9af507f2c68ac4f0cc80b1d2e38d2a51
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="maintaining-security"></a>維護安全性

常有人說，安全性的代價就是長期的警覺， 儘管您在應用程式的設計和開發過程中已經對安全性投注極大的心力，仍應該假設部署之後會產生安全性問題。 藉由稽核應用程式和分析事件記錄檔的方式，您可能會發現一些之前隱藏的問題。

此外，您不僅必須對自己的應用程式保持警覺心，也必須對執行應用程式的平台和應用程式相依的其他產品，注意其當前的安全性威脅和問題。

[安全性、隱私權和帳戶](https://support.microsoft.com/products/microsoft-account?category=privacy#security-privacy-accounts-help=windows-8&v0h=winrttab1&v1h=win8tab1&v2h=win7tab1&v3h=winvistatab1)&mdash;取得安全性、隱私權和使用者帳戶的說明，包含病毒、密碼、家長監護、防火牆和磁碟機加密的相關資訊。

[Microsoft 安全性更新公告](https://technet.microsoft.com/security/bulletins.aspx)&mdash;這個網頁可讓您輕鬆尋找之前發行的公告內容。 安全性佈告欄是專門為 IT 專業人員所設計，會提供關於安全性更新的詳細資訊。

[Microsoft Baseline Security Analyzer](https://www.microsoft.com/download/details.aspx?id=7558)&mdash;Microsoft Baseline Security Analyzer (MBSA) 是一種工具，可以讓個別的家庭使用者、公司使用者或系統管理員，針對一般的安全性組態錯誤，掃描一或多部 Windows 電腦。