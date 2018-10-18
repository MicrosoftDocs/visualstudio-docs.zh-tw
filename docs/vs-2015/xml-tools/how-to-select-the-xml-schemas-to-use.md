---
title: 如何： 選取要使用的 XML 結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5300623e3bbd1eeec584b30015e122539a6c7203
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210453"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>HOW TO：選取要使用的 XML 結構描述
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML 編輯器提供位於 %InstallDir%\Xml\Schemas 目錄的結構描述快取。 結構描述快取包括用於 IntelliSense 及 XML 文件驗證的常見 XML 結構描述。  
  
 **結構描述**文件屬性用來選取一或多個 XML 結構描述定義語言 (XSD) 結構描述使用。 它可讓您從結構描述快取中選取結構描述，或指定快取中沒有的結構描述。  
  
 您所指定的結構描述與其他所有 XML 文件屬性，會一起儲存在隱藏的解決方案使用者選項檔 (.suo) 中。 因此，在下次開啟解決方案時無需重新輸入這些值。  
  
> [!NOTE]
>  編輯器可使用內嵌結構描述，或由 `xsd:schemaLocation` 屬性參考的結構描述進行驗證。 如需詳細資訊，請參閱 < [XML 文件驗證](../xml-tools/xml-document-validation.md)。  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取選取 XML 結構描述  
  
1.  在 XML 編輯器中開啟檔案。  
  
2.  在 [文件屬性] 視窗中，按一下按鈕上**結構描述**欄位。  
  
     **XML 結構描述**對話方塊隨即出現。 對話方塊會列出具有.xsd 副檔名 （包括 catalog.xml 檔案中參考的結構描述） 結構描述快取中的所有結構描述，也會在目前的方案中，任何結構描述 Visual Studio 中開啟，在參考`xsd:schemaLocation`所參考或屬性，**結構描述**屬性。  
  
3.  請進行下列任一操作，以選取用於驗證的結構描述：  
  
    -   選取結構描述中所列**XML 結構描述** 對話方塊中，按一下**使用**資料行，然後選取**使用這個結構描述**。  
  
     -或-  
  
    -   選取多個結構描述中所列**XML 結構描述**對話方塊，以滑鼠右鍵按一下並選取**使用這個結構描述**。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
     選取的結構描述的清單複製回**結構描述**文件屬性。  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>若要將 XML 結構描述加入結構描述快取中  
  
1.  在 [文件屬性] 視窗中，按一下按鈕上**結構描述**欄位。  
  
2.  按一下 [加入] 。  
  
     這會開啟**開啟 XSD 結構描述**對話方塊。  
  
3.  瀏覽並選取要加入到結構描述快取中的結構描述。  
  
4.  按一下 **開啟**。  
  
     結構描述會加入至結構描述快取，而且**使用**資料行值設定為**使用這個結構描述**。  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取刪除 XML 結構描述  
  
1.  在 [文件屬性] 視窗中，按一下按鈕上**結構描述**欄位。  
  
2.  選取的結構描述中移除，然後按一下**移除**。  
  
     結構描述會從記憶體中的結構描述快取移除，但不會從檔案系統中移除。  
  
    > [!NOTE]
    >  如果您仍需透過結構描述參考`schemaLocation`屬性，或比對`targetNamespace`再**移除**不適用於這種情況，因為自動關聯。 在此情況下建議您將標示為結構描述**請勿使用選取的結構描述**中**使用**資料行。  
  
## <a name="see-also"></a>另請參閱  
 [結構描述快取](../xml-tools/schema-cache.md)   
 [XML 結構描述 對話方塊](../xml-tools/xml-schemas-dialog-box.md)   
 [XML 編輯器](../xml-tools/xml-editor.md)



