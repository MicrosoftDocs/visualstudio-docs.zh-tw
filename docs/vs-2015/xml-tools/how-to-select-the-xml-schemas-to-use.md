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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666512"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>HOW TO：選取要使用的 XML 結構描述
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 編輯器提供位於 %InstallDir%\Xml\Schemas 目錄的結構描述快取。 結構描述快取包括用於 IntelliSense 及 XML 文件驗證的常見 XML 結構描述。

 **架構**文件屬性是用來選取一或多個 XML 架構定義語言 (XSD) 架構 (s) 使用。 它可讓您從結構描述快取中選取結構描述，或指定快取中沒有的結構描述。

 您所指定的結構描述與其他所有 XML 文件屬性，會一起儲存在隱藏的解決方案使用者選項檔 (.suo) 中。 因此，在下次開啟解決方案時無需重新輸入這些值。

> [!NOTE]
> 編輯器可使用內嵌結構描述，或由 `xsd:schemaLocation` 屬性參考的結構描述進行驗證。 如需詳細資訊，請參閱 [XML 檔驗證](../xml-tools/xml-document-validation.md)。

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取選取 XML 結構描述

1. 在 XML 編輯器中開啟檔案。

2. 在 [檔案屬性] 視窗中，按一下 [ **架構** ] 欄位上的按鈕。

    [ **XML 架構** ] 對話方塊隨即顯示。 此對話方塊會在架構快取中列出具有 .xsd 副檔名的所有架構 (包括 catalog.xml 檔) 所參考的架構，以及目前方案中的任何架構、在 Visual Studio 中開啟、在屬性中參考， `xsd:schemaLocation` 或在 [ **架構** ] 屬性中參考。

3. 請進行下列任一操作，以選取用於驗證的結構描述：

   - 選取 [ **XML 架構** ] 對話方塊中所列的架構，按一下 [ **使用** ] 資料行，然後選取 [ **使用此架構**]。

     -或-

   - 選取 [ **XML 架構** ] 對話方塊中所列的多個架構，以滑鼠右鍵按一下並選取 [ **使用此架構**]。

4. 按一下 [確定]  。

    選取的架構清單會複製回 **架構** 檔案屬性。

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>若要將 XML 結構描述加入結構描述快取中

1. 在 [檔案屬性] 視窗中，按一下 [ **架構** ] 欄位上的按鈕。

2. 按一下 [新增] 。

     這會開啟 [ **開啟 XSD 架構** ] 對話方塊。

3. 瀏覽並選取要加入到結構描述快取中的結構描述。

4. 按一下 [開啟]。

     架構 (s) 加入至架構快取，而 [ **使用** ] 資料行值則設為 [ **使用此架構**]。

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>若要從結構描述快取刪除 XML 結構描述

1. 在 [檔案屬性] 視窗中，按一下 [ **架構** ] 欄位上的按鈕。

2. 選取要移除的架構，然後按一下 [ **移除**]。

     結構描述會從記憶體中的結構描述快取移除，但不會從檔案系統中移除。

    > [!NOTE]
    > 如果您仍有透過屬性的架構參考 `schemaLocation` ，或比 `targetNamespace` 對，則在這種情況下， **移除** 將無法在此情況下運作，因為會自動關聯。 在此情況下，建議您將架構標示為不要 **使用** [ **使用** ] 資料行中選取的架構。

## <a name="see-also"></a>另請參閱
 [架構](../xml-tools/schema-cache.md)快取 [XML 架構對話方塊](../xml-tools/xml-schemas-dialog-box.md) [XML 編輯器](../xml-tools/xml-editor.md)
