---
title: 選項、文字編輯器、HTML (Web Form)、驗證
description: 瞭解如何使用 [HTML] 區段中的 [驗證] 頁面，設定 HTML 編輯器如何檢查檔中 HTML 標籤語法的喜好設定。
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b65edc2b6c48bc76075e909d0f9bd1341a1b6dd8
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040559"
---
# <a name="options-text-editor-html-web-forms-validation"></a>選項、文字編輯器、HTML (Web Form)、驗證

使用 [驗證] 選項頁面來設定 HTML 編輯器如何檢查文件中 HTML 標記語法的喜好設定。 若要存取此頁面，請在功能表列上選擇 [**工具**  >  **選項**]，然後展開 [**文字編輯器**  >  **HTML (Web Form)**  >  **驗證**]。

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
