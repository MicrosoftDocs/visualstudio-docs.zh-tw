---
title: 如何-建立 ClickOnce 應用程式的檔案關聯 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76ecc41a852d80319f8a171ed590eb73680d92cc
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382493"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>How to: Create file associations for a ClickOnce application (如何：建立 ClickOnce 應用程式的檔案關聯)
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式可以與一個或多個副檔名相關聯，如此一來，當使用者開啟這些類型的檔案時，應用程式就會自動啟動。 將副檔名支援新增至 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式相當簡單。

### <a name="to-create-file-associations-for-a-clickonce-application"></a>若要建立 ClickOnce 應用程式的檔案關聯

1. 以一般方式建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，或使用您現有的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。

2. 使用文字或 XML 編輯器（如 [記事本]）開啟應用程式資訊清單。

3. 尋找 `assembly` 元素。 如需詳細資訊，請參閱 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。

4. 加入元素做為專案的子系 `assembly` `fileAssociation` 。 `fileAssociation`元素具有四個屬性：

   - `extension`：您想要與應用程式建立關聯的副檔名。

   - `description`：檔案類型的描述，會出現在 Windows shell 中。

   - `progid`：唯一識別檔案類型的字串，用來將它標示在登錄中。

   - `defaultIcon`：要用於此檔案類型的圖示。 在應用程式資訊清單中，必須將圖示新增為檔案資源。 如需詳細資訊，請參閱[如何：在 ClickOnce 應用程式中包含資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。

     如需 `file` 和元素的範例 `fileAssociation` ，請參閱[ \<fileAssociation> 元素](../deployment/fileassociation-element-clickonce-application.md)。

5. 如果您想要將多個檔案類型與應用程式建立關聯，請新增額外的 `fileAssociation` 元素。 請注意， `progid` 每個的屬性應該都不同。

6. 當您完成應用程式資訊清單之後，請重新簽署資訊清單。 您可以從命令列使用*Mage.exe*來執行這項操作。

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    如需詳細資訊，請參閱[Mage.exe （資訊清單產生和編輯工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)。

## <a name="see-also"></a>另請參閱
- [\<fileAssociation>元素](../deployment/fileassociation-element-clickonce-application.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
- [Mage.exe （資訊清單產生和編輯工具）](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)