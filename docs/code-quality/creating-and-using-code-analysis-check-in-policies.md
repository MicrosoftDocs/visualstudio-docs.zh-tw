---
title: "建立和使用程式碼分析簽入原則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a7d8ab4732938721da8e72c5a4c5f7387a4e67e2
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>建立和使用程式碼分析簽入原則
當您使用 Team Foundation 版本控制 (TFVC) 時，您可以建立.net 和原生 （C/c + +） 程式碼專案的 team 專案中的程式碼分析簽入原則。 您可以使用程式碼分析簽入原則，控制及改善已簽入程式碼基底的程式碼的品質。  
  
 當本機組建是最新和最新的來源檔案上已執行程式碼分析，原則將會成功。 最少的程式碼專案中已啟用程式碼分析規則必須包含與 team 專案簽入原則中所定義的相同規則。 規則被指定為 Team 專案設定中的錯誤，也必須指定為程式碼專案中的錯誤  
  
> [!IMPORTANT]
>  程式碼分析簽入原則無法套用至網站專案。 可以將它們套用至 web 應用程式專案。  
  
 您所使用的 Team 專案設定建立程式碼分析簽入原則[!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]。 指定並針對 team 專案時，強制執行簽入原則，但是設定和在本機開發電腦上執行的個別程式碼專案中的程式碼分析回合。 本章節描述如何指定程式碼分析簽入原則，針對 team 專案，以及如何實作自訂程式碼分析原則，針對 managed 程式碼。  
  
## <a name="in-this-section"></a>本章節內容  
 [如何：建立或更新標準程式碼分析簽入原則](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 說明您用來設定和修改 team 專案的程式碼分析原則的步驟。  
  
 [為 Managed 程式碼實作自訂簽入原則](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 說明您用來建立自訂規則集簽入原則的 team 專案時，並簽入原則與同步處理的 team 專案程式碼專案的步驟。  
  
 [程式碼分析簽入原則的版本相容性](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 說明程式碼分析簽入相容性問題的版本之間[!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)]。  
  
 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 說明如何將文字和語彙基元新增至字典中的程式碼分析命名規則所參考。  
  
## <a name="related-sections"></a>相關章節  
 [使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)