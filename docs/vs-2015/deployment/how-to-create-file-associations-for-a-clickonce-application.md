---
title: 作法：建立 ClickOnce 應用程式的檔案關聯 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82ffecdc719dad2f38208de00dc95438b3ff36ef
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697706"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>作法：建立 ClickOnce 應用程式的檔案關聯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式可以與一或多個檔案名稱副檔名，相關聯，以便在使用者開啟這些類型的檔案時應用程式也會自動啟動。 新增檔案副檔名支援以[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式很簡單。  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>若要建立 ClickOnce 應用程式的檔案關聯  
  
1. 建立[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式一般，或使用現有[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式。  
  
2. 使用文字編輯器或 XML 編輯器，例如 [記事本] 中開啟應用程式資訊清單。  
  
3. 尋找 `assembly` 項目。 如需詳細資訊，請參閱 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。  
  
4. 為子系`assembly`項目，新增`fileAssociation`項目。 `fileAssociation`項目有四個屬性：  
  
   - `extension`：您想要關聯到應用程式檔案名稱的副檔名。  
  
   - `description`：檔案類型，將會出現在 Windows shell 中的描述。  
  
   - `progid`：字串，用來唯一識別檔案類型，將它標記在登錄中。  
  
   - `defaultIcon`：若要使用此檔案類型圖示。 圖示必須新增為應用程式資訊清單中的檔案資源。 如需詳細資訊，請參閱[如何：在 ClickOnce 應用程式中納入資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。  
  
     如需`file`並`fileAssociation`項目，請參閱[ \<fileAssociation > 項目](../deployment/fileassociation-element-clickonce-application.md)。  
  
5. 如果您想要一個以上的檔案類型關聯到應用程式，加入額外`fileAssociation`項目。 請注意，`progid`屬性應該為每個不同。  
  
6. 完成與應用程式資訊清單所述，重新簽署資訊清單。 您可以從命令列完成這使用 Mage.exe。  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    如需詳細資訊，請參閱 [Mage.exe (資訊清單產生和編輯工具)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>另請參閱  
 [\<fileAssociation > 項目](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (資訊清單產生和編輯工具)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
