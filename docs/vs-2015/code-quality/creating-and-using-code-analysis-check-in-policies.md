---
title: 建立和使用程式碼分析簽入原則 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b2eb5059d5ec027654b1e4de7098c732e897088
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238351"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>建立和使用程式碼分析簽入原則
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您使用 Team Foundation 版本控制 (TFVC) 時，您可以建立.NET Framework 和原生 （C/c + +） 程式碼專案的 team 專案中的程式碼分析簽入原則。 您可以使用程式碼分析簽入原則來控制及改善簽入程式碼基底的程式碼品質。  
  
 當本機組建是最新狀態，並已執行的最新的來源檔案的程式碼分析時，就會通過此原則。 最少的程式碼專案中已啟用程式碼分析規則都必須包含相同的 team 專案簽入原則中所定義的規則。 在被指定為 Team 專案設定中的錯誤的規則也必須指定為程式碼專案中的錯誤  
  
> [!IMPORTANT]
>  程式碼分析簽入原則不適用於網站專案。 它們可以套用至 web 應用程式專案。  
  
 您使用的 Team 專案設定來建立程式碼分析簽入原則[!INCLUDE[esprscc](../includes/esprscc-md.md)]。 簽入原則指定，並針對 team 專案時，強制執行，但設定程式碼分析回合而且在本機開發電腦上執行的個別程式碼專案。 本章節描述如何指定程式碼分析簽入原則，為 team 專案以及如何實作 managed 程式碼的自訂程式碼分析原則。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立或更新標準程式碼分析簽入原則](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 說明您用來設定和修改 team 專案的程式碼分析原則的步驟。  
  
 [為受控程式碼實作自訂簽入原則](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 說明您用來建立自訂規則集的 team 專案簽入原則，以及與簽入原則同步處理的 team 專案的程式碼專案的步驟。  
  
 [程式碼分析簽入原則的版本相容性](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 說明版本之間的程式碼分析簽入相容性問題[!INCLUDE[vstsLong](../includes/vstslong-md.md)]。  
  
 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 說明如何將字組和語彙基元新增至字典中的程式碼分析命名規則所參考。  
  
## <a name="related-sections"></a>相關章節  
 [品質嚴格把關](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)



