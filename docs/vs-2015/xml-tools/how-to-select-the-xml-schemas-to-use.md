---
title: 如何：選取要使用的 XML 架構 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666512"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>HOW TO：選取要使用的 XML 結構描述
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 編輯器提供位於 %InstallDir%\Xml\Schemas 目錄的結構描述快取。 結構描述快取包括用於 IntelliSense 及 XML 文件驗證的常見 XML 結構描述。

 [**架構**檔] 屬性是用來選取要使用的一或多個 XML 架構定義語言（XSD）架構。 它可讓您從結構描述快取中選取結構描述，或指定快取中沒有的結構描述。

 您所指定的結構描述與其他所有 XML 文件屬性，會一起儲存在隱藏的解決方案使用者選項檔 (.suo) 中。 因此，在下次開啟解決方案時無需重新輸入這些值。

> [!NOTE]
> 編輯器可使用內嵌結構描述，或由 `xsd:schemaLocation` 屬性參考的結構描述進行驗證。 如需詳細資訊，請參閱[XML 檔驗證](../xml-tools/xml-document-validation.md)。

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取選取 XML 結構描述

1. 在 XML 編輯器中開啟檔案。

2. 在 [檔案屬性] 視窗中，按一下 [**架構**] 欄位上的 [] 按鈕。

    [ **XML 架構**] 對話方塊隨即顯示。 此對話方塊會列出架構快取中所有具有 .xsd 副檔名的架構（包括 catalog .xml 檔案中所參考的架構），以及目前方案中的任何架構、在 Visual Studio 中開啟、在 `xsd:schemaLocation` 屬性中參考，或在**架構**屬性。

3. 請進行下列任一操作，以選取用於驗證的結構描述：

   - 選取 [ **XML 架構**] 對話方塊中所列的架構，按一下 [**使用**] 資料行，然後選取 [**使用此架構**]。

     -或-

   - 選取 [ **XML 架構**] 對話方塊中所列的多個架構，以滑鼠右鍵按一下並選取 [**使用此架構**]。

4. 按一下 [確定]。

    選取的架構清單會複製回 [**架構**檔] 屬性。

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>若要將 XML 結構描述加入結構描述快取中

1. 在 [檔案屬性] 視窗中，按一下 [**架構**] 欄位上的 [] 按鈕。

2. 按一下 [加入]。

     這會開啟 [**開啟 XSD 架構**] 對話方塊。

3. 瀏覽並選取要加入到結構描述快取中的結構描述。

4. 按一下 [開啟]。

     已新增至架構快取的架構，而 [**使用**] 資料行值則設定為**使用此架構**。

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取刪除 XML 結構描述

1. 在 [檔案屬性] 視窗中，按一下 [**架構**] 欄位上的 [] 按鈕。

2. 選取要移除的架構，然後按一下 [**移除**]。

     結構描述會從記憶體中的結構描述快取移除，但不會從檔案系統中移除。

    > [!NOTE]
    > 如果您仍有透過 `schemaLocation` 屬性的架構參考，或符合的 `targetNamespace` 則在這種情況下，將無法使用 [**移除**]，因為自動關聯。 在此情況下，建議您在 [**使用**] 資料行中將架構標示為 [不要**使用選取的架構**]。

## <a name="see-also"></a>請參閱
 [架構](../xml-tools/schema-cache.md)快取[xml 架構對話方塊](../xml-tools/xml-schemas-dialog-box.md) [xml 編輯器](../xml-tools/xml-editor.md)
