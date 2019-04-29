---
title: HOW TO：選取要使用的 XML 結構描述
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41f830214b20df24587cf902e6b180e8a43a8cd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007387"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>HOW TO：選取要使用的 XML 結構描述

XML 編輯器提供位於結構描述快取 *%VSInstallDir%\xml\Schemas*目錄。 結構描述快取包括用於 IntelliSense 及 XML 文件驗證的常見 XML 結構描述。

使用**結構描述**文件來選取一或多個 XML 結構描述定義語言 (XSD) 結構描述的屬性。 您可以選取從結構描述快取或其他位置的結構描述。

您指定的結構描述會儲存在 （隱藏） 的解決方案使用者選項檔 (。*suo*)，以及所有其他 XML 文件屬性。 如此一來，您不必重新輸入這些值的下次開啟解決方案。

> [!NOTE]
> 編輯器可以使用內嵌結構描述或所參考的結構描述進行驗證`xsd:schemaLocation`屬性。 如需詳細資訊，請參閱 < [XML 文件驗證](../xml-tools/xml-document-validation.md)。

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取選取 XML 結構描述

1. 在 XML 編輯器中開啟檔案。

2. 在 [文件屬性] 視窗中，按一下**結構描述**欄位。 瀏覽按鈕 （...） 時出現，請按一下它。

   ![如需 XML 檔案的結構描述屬性](media/properties-schemas.png)

   [XML 結構描述 對話方塊](xml-schemas-dialog-box.md)隨即開啟。 對話方塊會列出所有的結構描述。*xsd*結構描述快取中的擴充功能 (包括結構描述中參考*catalog.xml*檔案)，也會在目前方案中，開啟在 Visual Studio 中參考之任何結構描述和`xsd:schemaLocation`屬性，或參考中**結構描述**屬性。

3. 請進行下列任一操作，以選取用於驗證的結構描述：

   - 選取結構描述中所列**XML 結構描述** 對話方塊中，按一下**使用**資料行，然後選取**使用這個結構描述**。

     -或-

   - 選取多個結構描述中所列**XML 結構描述** 對話方塊中，然後以滑鼠右鍵按一下並選取**使用這個結構描述**。

4. 選擇 [確定] 。

   選取的結構描述的清單複製回**結構描述**文件屬性。

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>將 XML 結構描述新增至結構描述快取

1. 在 [文件屬性] 視窗中，按一下按鈕上**結構描述**欄位。

2. 按一下 [加入] 。

   **開啟 XSD 結構描述** 對話方塊隨即開啟。

3. 瀏覽並選取要加入到結構描述快取中的結構描述。

4. 按一下 [開啟]。

   結構描述會加入至結構描述快取並**使用**資料行值設定為**使用這個結構描述**。

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取刪除 XML 結構描述

1. 在 [文件屬性] 視窗中，按一下按鈕上**結構描述**欄位。

2. 選取的結構描述中移除，然後按一下**移除**。

   結構描述會從記憶體中的結構描述快取移除，但不會從檔案系統中移除。

   > [!NOTE]
   > 如果您仍需透過結構描述參考`schemaLocation`屬性，或比對`targetNamespace`再**移除**不適用於這種情況，因為自動關聯。 在此情況下建議您將標示為結構描述**請勿使用選取的結構描述**中**使用**資料行。

## <a name="see-also"></a>另請參閱

- [結構描述快取](../xml-tools/schema-cache.md)
- [XML 結構描述 對話方塊](../xml-tools/xml-schemas-dialog-box.md)
- [XML 編輯器](../xml-tools/xml-editor.md)