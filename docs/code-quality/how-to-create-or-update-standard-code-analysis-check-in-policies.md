---
title: "如何： 建立或更新標準程式碼分析簽入原則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.policyeditor
helpviewer_keywords: code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d11a8c3169b019ac504ed98258d9281037eb1dd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>如何：建立或更新標準程式碼分析簽入原則
您可以要求中的所有程式碼專案的 team 專案執行程式碼分析，使用程式碼分析簽入原則。 需要程式碼分析可以改善已簽入程式碼基底程式碼的品質。  
  
> [!NOTE]
>  只有當您使用 Team Foundation Server 時，才使用這項功能。  
  
 程式碼分析簽入原則在 team 專案設定中設定，並套用至每一個 team 專案中的程式碼專案。 程式碼分析回合的程式碼專案的專案 (.xxproj) 檔中的程式碼專案設定。 在本機電腦上執行的程式碼分析回合。 Team 專案設定中的規則時啟用程式碼分析簽入原則、 其上次的編輯之後必須編譯要簽入程式碼專案中的檔案和包含執行的程式碼分析，至少必須在電腦上執行，c已進行 hanges。  
  
-   Managed 程式碼，您必須設定簽入原則藉由指定*規則集*，其中包含程式碼分析規則的子集。  
  
-   C/c + + 程式碼，簽入原則要求所有的程式碼分析規則會執行。 您可以加入前置處理器指示詞，若要停用個別的程式碼專案，在您的 team 專案中的特定規則。  
  
 指定 managed 程式碼簽入原則之後，小組成員可以同步處理程式碼專案的 team 專案的原則設定的程式碼分析設定。  
  
### <a name="to-open-the-check-in-policy-editor"></a>若要開啟簽入原則編輯器  
  
1.  在 Team Explorer 中 team 專案名稱上按一下滑鼠右鍵，指向**Team 專案設定**，然後按一下 **原始檔控制**。  
  
2.  在**原始檔控制**對話方塊中，選取**簽入原則** 索引標籤。  
  
3.  執行下列任一步驟：  
  
    -   按一下**新增**，建立新的簽入原則。  
  
    -   按兩下現有**程式碼分析**中的項目**原則類型**變更原則的清單。  
  
### <a name="to-set-policy-options"></a>若要設定原則選項  
  
-   選取或清除下列選項：  
  
    |選項|描述|  
    |------------|-----------------|  
    |**強制執行簽入以僅包含屬於目前方案的檔案。**|只有在方案和專案的組態檔中指定的檔案，可以執行程式碼分析。 此原則可確保分析的所有程式碼都是方案的一部分。|  
    |**強制執行 C/c + + 程式碼分析 (/analyze)**|需要所有的 C 或 c + + 專案，以建置 / analyze 編譯器選項，簽入之前執行程式碼分析。|  
    |**針對 Managed 程式碼強制執行程式碼分析**|需要所有的 managed 的專案執行程式碼分析，並建置簽入之前。|  
  
-  
  
### <a name="to-specify-a-managed-rule-set"></a>若要指定受管理的規則集  
  
-   從**執行此規則集**清單中，使用下列方法之一：  
  
    -   選取 Microsoft 標準規則集。  
  
    -   若要選取自訂規則集，請按一下**\<選取規則集從原始檔控制...>**，然後輸入 原始檔控制瀏覽器中的規則集的版本控制路徑。 版本控制路徑的語法如下：  
  
    -   **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    -   如需有關如何建立及實作自訂簽入原則規則設定，請參閱[Managed 程式碼的實作自訂簽入原則](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)。  
  
## <a name="see-also"></a>請參閱  
 [建立和使用程式碼分析簽入原則](../code-quality/creating-and-using-code-analysis-check-in-policies.md)