---
title: 新增檔案標頭
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c69f73989e898c44bdef6cf008d48f6c918652a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801317"
---
# <a name="add-file-header"></a>新增檔案標頭

此程式碼產生適用於：

- C#

- Visual Basic

事項 **：** 使用[EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project)將檔案標頭新增至現有的檔案、專案和方案。

時機 **：** 您想要輕鬆地將檔案標頭新增至檔案、專案和方案。

**原因：** 您的小組要求您針對著作權用途納入檔案標頭。 

## <a name="how-to"></a>操作方式

1. 將 [EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project) 新增至專案或方案（如果您還沒有的話）。

2. 在 EditorConfig 檔案中新增下列規則： *file_header_template*。

3. 將規則的值設定為等於您要套用的標頭文字。 您可以使用 `{fileName}` 做為檔案名的預留位置。

    ![EditorConfig 檔案標頭規則](media/add-file-header-rule.png)

    > [!NOTE]
    > 您在 EditorConfig 中不能有明確的 multilines，而且必須使用 Unix 換行字元來插入新的行。

4. 將您的插入號放在任何 c # 或 Visual Basic 檔案的第一行。

5. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

6. 選取 [ **新增檔案標頭**]。 

    ![EditorConfig 檔案標頭規則](media/add-file-header.png)

7. 若要將檔案標頭套用至整個專案或方案，請在 [**修正所有出現**的專案：] 選項下，選取 [**專案**] 或 [**方案**]。

8. [ **修正所有出現** 專案] 對話方塊隨即開啟，您可以在其中預覽變更。

    ![修正所有出現的對話方塊](media/file-header-preview-changes.png)

8. 選取 **[** 套用] 以套用變更。

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
