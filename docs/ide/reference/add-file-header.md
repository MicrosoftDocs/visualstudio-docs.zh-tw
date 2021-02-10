---
title: 新增檔案標頭
description: 瞭解如何使用 EditorConfig 檔案，將檔案標頭新增至現有的檔案、專案和方案。
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2b177092b04d5042f62dfd0b34d2bfbf4f1f0228
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933865"
---
# <a name="add-file-header"></a>新增檔案標頭

此程式碼產生適用於：

- C#

- Visual Basic

事項 **：** 使用 [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)將檔案標頭新增至現有的檔案、專案和方案。

時機 **：** 您想要輕鬆地將檔案標頭新增至檔案、專案和方案。

**原因：** 您的小組要求您針對著作權用途納入檔案標頭。 

## <a name="how-to"></a>使用方法

1. 將 [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) 新增至專案或方案（如果您還沒有的話）。

2. 在 EditorConfig 檔案中新增下列規則： *file_header_template*。

3. 將規則的值設定為等於您要套用的標頭文字。 您可以使用 `{fileName}` 做為檔案名的預留位置。

    ![顯示 file_header_template 值之 EditorConfig 檔案的螢幕擷取畫面。](media/add-file-header-rule.png)

    > [!NOTE]
    > 您在 EditorConfig 中不能有明確的 multilines，而且必須使用 Unix 換行字元來插入新的行。

4. 將您的插入號放在任何 c # 或 Visual Basic 檔案的第一行。

5. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

6. 選取 [ **新增檔案標頭**]。 

    ![[新增檔案標頭] 選項的螢幕擷取畫面。](media/add-file-header.png)

7. 若要將檔案標頭套用至整個專案或方案，請在 [**修正所有出現** 的專案：] 選項下，選取 [**專案**] 或 [**方案**]。

8. [ **修正所有出現** 專案] 對話方塊隨即開啟，您可以在其中預覽變更。

    ![修正所有出現的對話方塊](media/file-header-preview-changes.png)

8. 選取 **[** 套用] 以套用變更。

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)