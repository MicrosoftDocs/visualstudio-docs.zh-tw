---
title: 檢視類型定義
ms.date: 01/10/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ef13b959d4e106b451ea0cfb336835059667ce4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592070"
---
# <a name="view-type-and-member-definitions"></a>檢視型別與成員的定義

開發人員經常需要檢視他們在程式碼中使用的型別或類別成員的原始程式碼定義。 Visual Studio 中的 [移至定義]**** 和 [查看定義]**** 功能可讓您輕鬆地檢視型別或成員的定義。 如果無法取得原始程式碼，則改為顯示中繼資料。

## <a name="go-to-definition"></a>移至定義

**"轉到定義"** 功能導航到類型或成員的源，並在新選項卡中打開結果。如果您是鍵盤使用者，請將文本游標放在符號名稱的某處，然後按**F12**。 如果您是滑鼠使用者，請選取右鍵功能表中的 [移至定義]****，或使用下節所述的 **Ctrl+按一下滑鼠左鍵**功能。

### <a name="ctrl-click-go-to-definition"></a>Ctrl+按一下滑鼠左鍵移至定義

**Ctrl**+**點擊**是滑鼠使用者快速訪問**轉到定義的**快捷方式。 當您按 **Ctrl** 並將滑鼠指標移至類型和成員上方時，符號會變成可點選。 若要快速巡覽至符號的定義，請按 **Ctrl** 鍵，然後按一下它。 就是這麼簡單！

![滑鼠點按移至定義動畫](../ide/media/click_gotodef.gif)

您可以通過轉到 **"工具** > **選項** > **文字編輯器** > **"** 來更改滑鼠**按一下"轉到定義"** 的修飾符鍵，並從 **"使用修改器"鍵**下拉下下下下下下下下從"使用"鍵鍵下拉清單選擇**Alt**或**Ctrl**+**Alt。** 您也可以停用滑鼠點按 [移至定義]****，方法是取消核取 [Enable mouse click to perform Go To Definition] (啟用滑鼠點按以執行移至定義)**** 核取方塊。

![啟用滑鼠點按移至定義](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>查看定義

[查看定義]**** 功能可讓您預覽類型的定義，而不需要離開編輯器中的目前位置。 如果您是鍵盤使用者，請將文字游標放在類型或成員名稱內的某個位置，然後按 **Alt + F12**。 如果您是使用滑鼠使用者，則可選取右鍵功能表中的 [查看定義]****。

要啟用**Ctrl**+**按一下**功能，請轉到**工具** > **選項** > **文字編輯器** > **總編**。 選取 [Open definition in peek view] (在查看檢視中開啟定義)**** 選項，然後按一下 [確定]**** 關閉 [選項]**** 對話方塊。

![設定滑鼠點按查看定義選項](../ide/media/editor_options_peek_view.png)

然後按 **Ctrl** (或 [選項]**** 中選取的輔助按鍵)，然後按一下類型或成員。

![查看定義動畫](../ide/media/peek_definition.gif)

如果您從快顯視窗查看另一個定義，則會啟動階層連結路徑；您可以使用快顯視窗上方的圓形和箭號進行巡覽。

如需詳細資訊，請參閱[如何：使用查看定義 (Alt+F12) 檢視和編輯程式碼](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)。

## <a name="view-metadata-as-source-code-c"></a>中繼資料視為原始程式碼 (C#)

當無法取得您檢視的 C# 型別或成員的原始程式碼時，會改為顯示其中繼資料。 您可以查看所宣告的型別和成員，但無法查看其實作。

當您針對無法取得原始程式碼定義的項目執行 [移至定義]**** 或 [查看定義]**** 命令時，程式碼編輯器中會顯示包含該項目中繼資料 (顯示為原始程式碼) 之索引標籤文件的檢視。 後面加上 **[來自中繼資料]** 的類型名稱會出現在文件的索引標籤上。

例如，如果對 <xref:System.Console> 執行 [移至定義]**** 命令，<xref:System.Console> 的中繼資料就會當做 C# 原始程式碼出現在程式碼編輯器中。 程式碼看起來像其宣告，但未顯示實作。

![中繼資料當做原始碼](../ide/media/metadatasource.png)

> [!NOTE]
> 當您嘗試對標記為內部的型別或成員執行 [移至定義]**** 或 [檢視定義]**** 命令時，Visual Studio 不會將它們的中繼資料顯示為原始程式碼，無論參考的組件是否為 Friend 組件。

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>檢視反編譯的原始定義而不是中繼資料 (C#)

您可以設定選項，以在檢視無法取得原始程式碼的 C# 類型或成員定義時，查看反向組譯的原始程式碼。 要打開此功能，請從功能表列中選擇 **"工具** > **選項**"。 然後，展開**文字編輯器** > **C#** > **高級**，然後選擇**啟用導航以取消編譯的源**。

![檢視反編譯的定義](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio 使用 ILSpy 反編譯來重新建構方法主體。 第一次存取此功能時，您必須同意有關軟體授權及著作權與商標法相關的免責聲明。

## <a name="see-also"></a>另請參閱

- [巡覽程式碼](../ide/navigating-code.md)
- [如何：使用查看定義 (Alt+F12) 檢視和編輯程式碼](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
