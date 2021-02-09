---
title: 選項、文字編輯器、JavaScript、專案
description: 瞭解如何使用 [選項] 對話方塊的 [專案] 頁面，在程式碼編輯器中指定 JavaScript 和 TypeScript 專案選項。
ms.custom: SEO-VS-2020
ms.date: 06/19/2020
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b30aaec3087cece63e392cf7170ac85f6be0ad7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932328"
---
# <a name="options-text-editor-javascript-project"></a>選項、文字編輯器、JavaScript、專案

使用 [選項] 對話方塊的 [專案] 頁面，在程式碼編輯器中指定 JavaScript 和 TypeScript 專案選項。 若要存取此頁面，請在功能表列上選擇 [**工具**  >  **選項**]，然後展開 [**文字編輯器**  >  **JavaScript/TypeScript**  >  **專案**]。

## <a name="project-analysis-options"></a>專案分析選項

這些選項決定編輯器如何分析專案、報告診斷，並建議改進的方式。 選取或清除選項以指定編輯器處理這些情況的方式。

### <a name="uielement-list"></a>UIElement 清單

- **僅分析包含在編輯器中開啟之檔案的專案**
- **僅報告在編輯器中開啟之檔案的診斷**
- **建議並非校正的可行改善**

## <a name="virtual-projects-in-solution-explorer"></a>[方案總管] 中的虛擬專案

這些選項可讓您選擇是否要在載入或未載入解決方案時顯示虛擬專案。

## <a name="compile-on-save"></a>儲存時編譯

這些選項會決定是否自動編譯不屬於專案一部分的 TypeScript 檔案。 Visual Studio 使用安裝在 *C:\Program 檔 (x86) \Microsoft SDKs\TypeScript* 中的最新 TypeScript 版本進行編譯。

選取該核取方塊，然後選擇要使用的程式碼產生類型。

### <a name="uielement-list"></a>UIElement 清單

- **對於不屬於專案的模組，請使用 AMD 程式碼產生**
- **對於不屬於專案的模組，請使用 CommonJS 程式碼產生**
- **對於不屬於專案的模組，請使用 UMD 程式碼產生**
- **對於不屬於專案的模組，請使用系統程式碼產生**
- **對於不屬於專案的模組，請使用 ES2015 程式碼產生**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>不屬於專案之檔案的 ECMAScript 版本

這些選項允許您為不屬於專案一部分的檔案選取 ECMAScript 版本。 您可以選擇 **ECMAScript 3**、**ECMAScript 5** 或 **ECMAScript 6**。

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>不屬於專案之 TSX 檔案的 JSX 發出

這些選項會決定編輯器如何處理不屬於專案一部分的 TypeScript 檔案。

### <a name="uielement-list"></a>UIElement 清單

|選項|Description|
|------------|-----------------|
|**React 架構**|選取此選項後，程式碼編輯器會發出 *.js* 副檔名。|
|**保存**|選取此選項時，程式碼編輯器會將 JSX 保留為輸出的一部分，並發出 *.jsx* 副檔名。|

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)