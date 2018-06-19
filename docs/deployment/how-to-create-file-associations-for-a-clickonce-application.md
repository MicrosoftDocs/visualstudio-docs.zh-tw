---
title: 如何： 建立 ClickOnce 應用程式的檔案關聯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf60327e622f8eb32757d29051e3dce94661722d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557758"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>如何：建立 ClickOnce 應用程式的檔案關聯
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以與一個或多個檔案名稱副檔名，相關聯，以便在使用者開啟這些類型的檔案時應用程式也會自動啟動。 新增檔案副檔名支援以[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式相當簡單。  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>若要建立檔案關聯的 ClickOnce 應用程式  
  
1.  建立[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式通常，或使用現有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。  
  
2.  使用文字編輯器或 XML 編輯器，例如 [記事本] 中開啟應用程式資訊清單。  
  
3.  尋找 `assembly` 項目。 如需詳細資訊，請參閱 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。  
  
4.  做為子系`assembly`項目，加入`fileAssociation`項目。 `fileAssociation`元素有四個屬性：  
  
    -   `extension`： 您想要關聯到應用程式檔案名稱副檔名。  
  
    -   `description`: 描述的檔案類型，會出現在 Windows shell 中。  
  
    -   `progid`： 用來唯一識別要標示在登錄中的檔案類型一個字串。  
  
    -   `defaultIcon`： 若要使用此檔案類型圖示。 圖示必須新增為檔案中的資源應用程式資訊清單。 如需詳細資訊，請參閱 [如何：在 ClickOnce 應用程式中納入資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。  
  
     如需`file`和`fileAssociation`項目，請參閱[ \<fileAssociation > 項目](../deployment/fileassociation-element-clickonce-application.md)。  
  
5.  如果您想要將一個以上的檔案類型與應用程式產生關聯，將其他`fileAssociation`項目。 請注意，`progid`屬性應該為每個不同。  
  
6.  一旦您完成應用程式資訊清單，請重新簽署資訊清單。 您可以從命令列使用 Mage.exe。  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     如需詳細資訊，請參閱[Mage.exe （資訊清單產生和編輯工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>另請參閱  
 [\<fileAssociation > 項目](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (資訊清單產生和編輯工具)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)