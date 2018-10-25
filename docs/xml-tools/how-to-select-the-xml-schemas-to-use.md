---
title: HOW TO：選取要使用的 XML 結構描述
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a04075c0625eb7b4dc899a4e183588b96eb7eadd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872235"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>如何： 選取要使用的 XML 結構描述

XML 編輯器提供位於結構描述快取 *%InstallDir%\Xml\Schemas*目錄。 結構描述快取包括用於 IntelliSense 及 XML 文件驗證的常見 XML 結構描述。

**結構描述**文件屬性用來選取一或多個 XML 結構描述定義語言 (XSD) 結構描述使用。 它可讓您從結構描述快取中選取結構描述，或指定快取中沒有的結構描述。

您指定的結構描述會儲存在隱藏的方案使用者選項檔 (。*suo*)，以及所有其他 XML 文件屬性。 因此，在下次開啟解決方案時無需重新輸入這些值。

> [!NOTE]
> 編輯器可使用內嵌結構描述，或由 `xsd:schemaLocation` 屬性參考的結構描述進行驗證。 如需詳細資訊，請參閱 < [XML 文件驗證](../xml-tools/xml-document-validation.md)。

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取選取 XML 結構描述

1. 在 XML 編輯器中開啟檔案。

2. 在 [文件屬性] 視窗中，按一下按鈕上**結構描述**欄位。

    **XML 結構描述**對話方塊隨即出現。 對話方塊會列出所有的結構描述。*xsd*結構描述快取中的擴充功能 (包括結構描述中參考*catalog.xml*檔案)，也會在目前方案中，開啟在 Visual Studio 中參考之任何結構描述和`xsd:schemaLocation`屬性，或參考中**結構描述**屬性。

3. 請進行下列任一操作，以選取用於驗證的結構描述：

   - 選取結構描述中所列**XML 結構描述** 對話方塊中，按一下**使用**資料行，然後選取**使用這個結構描述**。

     -或-

   - 選取多個結構描述中所列**XML 結構描述**對話方塊，以滑鼠右鍵按一下並選取**使用這個結構描述**。

4. 按一下 [確定 **Deploying Office Solutions**]。

    選取的結構描述的清單複製回**結構描述**文件屬性。

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>將 XML 結構描述新增至結構描述快取

1.  在 [文件屬性] 視窗中，按一下按鈕上**結構描述**欄位。

2.  按一下 [加入] 。

     這會開啟**開啟 XSD 結構描述**對話方塊。

3.  瀏覽並選取要加入到結構描述快取中的結構描述。

4.  按一下 **開啟**。

     結構描述會加入至結構描述快取，而且**使用**資料行值設定為**使用這個結構描述**。

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取刪除 XML 結構描述

1.  在 [文件屬性] 視窗中，按一下按鈕上**結構描述**欄位。

2.  選取的結構描述中移除，然後按一下**移除**。

     結構描述會從記憶體中的結構描述快取移除，但不會從檔案系統中移除。

    > [!NOTE]
    > 如果您仍需透過結構描述參考`schemaLocation`屬性，或比對`targetNamespace`再**移除**不適用於這種情況，因為自動關聯。 在此情況下建議您將標示為結構描述**請勿使用選取的結構描述**中**使用**資料行。

## <a name="see-also"></a>另請參閱

- [結構描述快取](../xml-tools/schema-cache.md)
- [XML 結構描述 對話方塊](../xml-tools/xml-schemas-dialog-box.md)
- [XML 編輯器](../xml-tools/xml-editor.md)