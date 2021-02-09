---
title: " (ClickOnce 應用程式建立檔案關聯) "
description: 瞭解如何將 ClickOnce 應用程式與一或多個副檔名產生關聯，讓應用程式在使用者開啟這類檔案時啟動。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b74e20d21ad2c67eed36add90051119c7b8b56e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861162"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>How to: Create file associations for a ClickOnce application (如何：建立 ClickOnce 應用程式的檔案關聯)
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可與一個或多個副檔名相關聯，如此一來，當使用者開啟這些類型的檔案時，就會自動啟動應用程式。 將副檔名支援新增至 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式很簡單。

### <a name="to-create-file-associations-for-a-clickonce-application"></a>建立 ClickOnce 應用程式的檔案關聯

1. 以一般方式建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，或使用您現有的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。

2. 使用文字或 XML 編輯器（例如 [記事本]）開啟應用程式資訊清單。

3. 尋找 `assembly` 元素。 如需詳細資訊，請參閱 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)。

4. 在專案的子系 `assembly` 中，加入 `fileAssociation` 元素。 `fileAssociation`元素有四個屬性：

   - `extension`：您想要與應用程式建立關聯的檔案名副檔名。

   - `description`：檔案類型的描述，它會出現在 Windows shell 中。

   - `progid`：唯一識別檔案類型的字串，可將它標示在登錄中。

   - `defaultIcon`：要用於此檔案類型的圖示。 圖示必須新增為應用程式資訊清單中的檔案資源。 如需詳細資訊，請參閱 [如何：在 ClickOnce 應用程式中包含資料檔案](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)。

     如需 `file` 和元素的範例 `fileAssociation` ，請參閱[ \<fileAssociation> 元素](../deployment/fileassociation-element-clickonce-application.md)。

5. 如果您想要將多個檔案類型與應用程式建立關聯，請新增其他 `fileAssociation` 元素。 請注意， `progid` 每個屬性都應該不同。

6. 當您完成應用程式資訊清單之後，請重新簽署資訊清單。 您可以使用 *Mage.exe* 從命令列進行這項作業。

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    如需詳細資訊，請參閱 [Mage.exe (資訊清單產生和編輯工具) ](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)。

## <a name="see-also"></a>另請參閱
- [\<fileAssociation> 元素](../deployment/fileassociation-element-clickonce-application.md)
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
- [Mage.exe (資訊清單產生和編輯工具) ](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)