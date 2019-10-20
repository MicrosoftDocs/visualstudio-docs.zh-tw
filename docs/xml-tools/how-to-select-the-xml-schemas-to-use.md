---
title: HOW TO：選取要使用的 XML 結構描述
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 275def786a93d42e6b8e110d3b3d785a24e948b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601903"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>如何：選取要使用的 XML 架構

XML 編輯器提供位於 *%VSInstallDir%\xml\Schemas*目錄中的架構快取。 結構描述快取包括用於 IntelliSense 及 XML 文件驗證的常見 XML 結構描述。

使用 [**架構**] document 屬性來選取一或多個 XML 架構定義語言（XSD）架構。 您可以從架構快取或其他位置選取架構。

您指定的架構會儲存在（隱藏）解決方案使用者選項檔案中（。 *.suo*）以及其他所有 XML 文件屬性。 因此，下次開啟方案時，您不需要重新輸入這些值。

> [!NOTE]
> 編輯器可以使用內嵌架構或 `xsd:schemaLocation` 屬性所參考的架構進行驗證。 如需詳細資訊，請參閱[XML 檔驗證](../xml-tools/xml-document-validation.md)。

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>若要從架構快取中選取 XML 架構

1. 在 XML 編輯器中開啟檔案。

2. 在 [檔案屬性] 視窗中，按一下 [**架構**] 欄位。 當瀏覽按鈕（...）出現時，按一下它。

   ![XML 檔案的架構屬性](media/properties-schemas.png)

   [ [XML 架構] 對話方塊](xml-schemas-dialog-box.md)隨即開啟。 對話方塊會列出具有的所有架構。架構快取中的*xsd*擴充功能（包括*目錄 .xml*檔案中所參考的架構），以及目前方案中的任何架構、在 Visual Studio 中開啟、在 `xsd:schemaLocation` 屬性中參考，或在**架構**中參考property.

3. 請進行下列任一操作，以選取用於驗證的結構描述：

   - 選取 [ **XML 架構**] 對話方塊中所列的架構，按一下 [**使用**] 資料行，然後選取 [**使用此架構**]。

     -或-

   - 選取 [ **XML 架構**] 對話方塊中所列的多個架構，然後以滑鼠右鍵按一下並選取 [**使用此架構**]。

4. 選擇 [確定]。

   選取的架構清單會複製回 [**架構**檔] 屬性。

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>若要將 XML 架構新增至架構快取

1. 在 [檔案屬性] 視窗中，按一下 [**架構**] 欄位上的 [] 按鈕。

2. 按一下 [加入]。

   [**開啟 XSD 架構**] 對話方塊隨即開啟。

3. 瀏覽並選取要加入到結構描述快取中的結構描述。

4. 按一下 [開啟]。

   架構會新增至架構快取，而 [**使用**] 資料行值則設定為**使用此架構**。

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>若要從架構快取中刪除 XML 架構

1. 在 [檔案屬性] 視窗中，按一下 [**架構**] 欄位上的 [] 按鈕。

2. 選取要移除的架構，然後按一下 [**移除**]。

   結構描述會從記憶體中的結構描述快取移除，但不會從檔案系統中移除。

   > [!NOTE]
   > 如果您仍有透過 `schemaLocation` 屬性的架構參考，或符合的 `targetNamespace` 則在這種情況下，將無法使用 [**移除**]，因為自動關聯。 在此情況下，建議您在 [**使用**] 資料行中將架構標示為 [不要**使用選取的架構**]。

## <a name="see-also"></a>請參閱

- [架構快取](../xml-tools/schema-cache.md)
- [[XML 架構] 對話方塊](../xml-tools/xml-schemas-dialog-box.md)
- [XML 編輯器](../xml-tools/xml-editor.md)