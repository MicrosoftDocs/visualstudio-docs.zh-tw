---
title: 選項、文字編輯器、HTML (Web Form)、驗證
ms.date: 1/15/2019
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f629a0b8d9f149ee10f7a35c75e351a6c3abfd3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031769"
---
# <a name="options-text-editor-html-web-forms-validation"></a>選項、文字編輯器、HTML (Web Form)、驗證

使用 [驗證] 選項頁面來設定 HTML 編輯器如何檢查文件中 HTML 標記語法的喜好設定。 若要存取此頁面，請在功能表列上依序選擇 [工具] > [選項]，然後依序展開 [文字編輯器] > [HTML (Web Form)] > [驗證]。

## <a name="validation"></a>驗證

- **將 doctype 用於驗證結構描述偵測**

   結構描述決定在該結構描述中有效的元素、屬性和大小寫。 也決定可在 IntelliSense 中使用哪些標籤和屬性。

   若您想要 Visual Studio 使用頁面的 **<!DOCTYPE>** 宣告與 **html** 元素來決定結構描述，請選取此選項。 例如，若您選取此選項且頁面有 `<!DOCTYPE html>` 宣告，則 Visual Studio 會使用 HTML5 結構描述。 不過，如果 **html** 標籤有 **xmlns** 屬性 (例如 `<html xmlns="http://www.w3.org/1999/xhtml">`)，則 Visual Studio 會使用 XHTML5 結構描述。

- **找不到 doctype 時的目標**

   選擇一個結構描述，當頁面中沒有 **<!DOCTYPE>** 宣告時，會使用它來驗證。

  - **顯示錯誤**

     選取核取方塊以啟用驗證。 如果未選取核取方塊，編輯器不會標示驗證錯誤。

     其他核取方塊可讓您微調驗證，您可以指定編輯器要標示的個別錯誤類型。

     > [!NOTE]
     > 部分結構描述不提供標記個別錯誤類型的選項。 例如，如果您選擇 **XHTML 1.1** 作為目標結構描述，則所有選項核取方塊都會停用。 在此情況下，系統會標示所有錯誤類型。

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)