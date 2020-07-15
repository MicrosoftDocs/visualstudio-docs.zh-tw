---
title: 新增檔案標頭
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 779092e277ac5b6eed3afcaceaf55b26ee2759dd
ms.sourcegitcommit: 025816f8e388b29e58761d304b0fda755ac5a613
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374165"
---
# <a name="add-file-header"></a>新增檔案標頭

此程式碼產生適用於：

- C#

- Visual Basic

**功能：** 使用[EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project)，將檔案標頭加入至現有的檔案、專案和方案。

時機 **：** 您想要輕鬆地將檔案標頭新增至檔案、專案和方案。

**原因：** 您的小組要求您包含檔案標頭以供著作權之用。 

## <a name="how-to"></a>操作方式

1. 如果您還沒有[EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project) ，請將它加入至專案或方案。

2. 將下列規則新增至您的 EditorConfig 檔案： *file_header_template*。

3. 將規則的值設定為等於您要套用的標頭文字。

    ![EditorConfig 檔案標頭規則](media/add-file-header-rule.png)

> [!NOTE]
> 您在 EditorConfig 中不能有明確的 multilines，而且必須使用 Unix 分行符號來插入新行。

4. 將插入號放在任何 c # 或 Visual Basic 檔案的第一行。

5. 按**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

6. 選取 [**新增檔案標頭**]。 

    ![EditorConfig 檔案標頭規則](media/add-file-header.png)

7. 若要將檔案標頭套用至整個專案或方案，請在 [**修正所有出現次數：** ] 選項底下選取 [**專案**] 或 [**方案**]。

8. [**修正所有出現次數**] 對話方塊會開啟，您可以在其中預覽變更。

    ![修正所有出現次數對話方塊](media/file-header-preview-changes.png)

8. 選取 **[** 套用] 以套用變更。

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
