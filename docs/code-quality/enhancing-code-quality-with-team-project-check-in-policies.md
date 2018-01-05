---
title: "強化程式碼品質，使用 Team 專案簽入原則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 36e0ab96c1c0c3deeced62ff9808737c903e682b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>使用 Team 專案簽入原則強化程式碼品質

當您使用 Team Foundation 版本控制 (TFVC) 時，您可以建立 Team 專案的簽入原則。 強制執行會得到較佳程式碼和較有效的團體開發的做法。 簽入原則是在 Team 專案層級設定的規則，而且會在允許程式碼簽入之前，於開發人員電腦上強制執行。

您可以指定這些 Team 專案簽入原則：

- **建置**：必須在新簽入之前修復在建置期間所建立的建置中斷。

- **變更集註解**：需要使用者在簽入變更時提供註解。

- **程式碼分析**：需要在簽入前先執行程式碼分析。

- **工作項目**：需要一或多個工作項目與此簽入建立關聯性。

> [!IMPORTANT]
> 若要使用簽入原則，您必須連接到 [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)]。

## <a name="common-tasks"></a>一般工作

|工作|支援內容|
|----------|------------------------|
|**建立和使用程式碼分析簽入原則：** 您可以從一組標準的程式碼分析規則中選擇，或者建立一組自訂規則。|[建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>相關工作

|工作|支援內容|
|----------|------------------------|
|**在開發過程中使用程式碼分析：** 小組成員在其開發電腦上執行程式碼分析。 在 Visual Studio 中，開發人員會針對個別程式碼專案設定並執行程式碼分析回合、檢視及分析回合中找到的問題，以及建立警告的工作項目。|[分析應用程式品質](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**建立及執行單元測試：** 單元測試提供一種快速的方法，讓開發人員和測試人員找出 C#、Visual Basic .NET 和 C++ 專案中類別方法的邏輯錯誤。 您只要建立一次單元測試，就可以在每次原始程式碼變更時執行，以確定沒有導入任何錯誤。|[對程式碼進行單元測試](../test/unit-test-your-code.md)|
|**追蹤工作項目和缺失：** 您可以使用工作項目追蹤和管理您的工作和 Team 專案相關資訊。 工作項目是資料庫記錄， [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] 用來追蹤指派和工作進度。 您可以使用不同類型的工作項目來追蹤不同類型的工作，例如客戶需求、產品錯誤及開發工作。|[工作項目 (VSTS)](/vsts/work/work-items/index)|

## <a name="external-resources"></a>外部資源

[使用 Visual Studio 2012 測試持續傳遞 - 第 2 章：單元測試：測試內部](http://go.microsoft.com/fwlink/?LinkID=255188)