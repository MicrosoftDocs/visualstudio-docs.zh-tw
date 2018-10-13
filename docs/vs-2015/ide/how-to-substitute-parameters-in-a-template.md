---
title: 如何：替代範本中的參數 | Microsoft Docs
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
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bab1d1fd7cd08813dadefbcbec27dbd84bd7b66b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279736"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>如何：替代樣板中的參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

根據範本建立檔案時，您可以取代範本參數 (例如類別名稱和命名空間)。 如需完整的範本參數清單，請參閱[範本參數](../ide/template-parameters.md)。  
  
## <a name="procedure"></a>程序  
 只要根據該範本建立專案時，就可能會取代範本檔案中的參數。 此程序說明使用範本建立新的專案時，如何建立將命名空間名稱取代為安全專案名稱的範本。  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>使用參數將命名空間名稱取代為專案名稱  
  
1.  在範本的一或多個程式碼檔案中，插入參數。 例如:   
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  以格式 $<參數>$ 撰寫範本參數。  
  
2.  在範本的 .vstemplate 檔案中，找出包括此檔案的 `ProjectItem` 項目。  
  
3.  將 `ProjectItem` 項目的 `ReplaceParameters` 屬性設定為 `true`。 例如:   
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [範本參數](../ide/template-parameters.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem 元素 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)



