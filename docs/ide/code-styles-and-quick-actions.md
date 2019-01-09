---
title: 程式碼樣式喜好設定
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: e1875099fa73fc994643b137807d1b0e1ed485c9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949942"
---
# <a name="code-style-preferences"></a>程式碼樣式喜好設定

從 [工具] 功能表中開啟 [選項] 對話方塊，以設定 C# 和 Visual Basic 專案的程式碼樣式喜好設定。 在 [選項] 對話方塊中，選取 [文字編輯器] > [C#] 或 [Basic] > [程式碼樣式] > [一般]。 在此視窗中設定的選項僅適用於本機電腦。

清單中的每個項目會在選取時顯示個別的喜好設定預覽：

![程式碼樣式選項](media/code-style-quick-actions-dialog.png)

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的編輯器行為](/visualstudio/mac/editor-behavior)。

## <a name="preference-and-severity"></a>喜好設定和嚴重性

對於各個項目，您可以使用每一行的下拉式清單來設定 [喜好設定] 和 [嚴重性] 的值。 [嚴重性] 可設定為 [無]、[建議]、[警告] 或 [錯誤]。 如果您想要針對程式碼樣式啟用[快速動作](../ide/quick-actions.md)，請務必將 [嚴重性] 設定為 [無] 以外的值。 當使用非慣用樣式時，會出現**快速動作**燈泡圖示![小燈泡圖示](media/vs2015_lightbulbsmall.png)，而您可以選擇 [快速動作] 清單上的選項，以自動將程式碼重寫成慣用的樣式。

## <a name="editorconfig-files"></a>EditorConfig 檔案

您也可以使用 [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) 檔案管理 .NET 程式碼樣式設定。 EditorConfig 檔案中設定的優先權高於 [選項] 對話方塊中選取的選項。 您可以使用 EditorConfig 檔案強制執行並設定整個存放庫或專案的程式碼撰寫樣式。

## <a name="format-document-command"></a>將文件格式化命令

在 Visual Studio 2017 15.8 及更新版本中，您可以設定**將文件格式化**命令 ([編輯] > [進階] > [將文件格式化]) 以對檔案執行額外的程式碼清理，例如移除及排序 using，或套用程式碼樣式喜好設定。 您可在 [[格式化] 選項頁面](reference/options-text-editor-csharp-formatting.md#format-document-settings)定義您希望**將文件格式化**套用哪些設定。

程式碼清理會遵循在 *.editorconfig* 檔案中進行的設定，若缺少該規則會檔案，則遵循 [工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] 或 [格式化] 中的設定。

當您初次在 Visual Studio 2017 中觸發**將文件格式化**命令時，黃色的資訊列會提示您進行程式碼清理設定。

> [!TIP]
> 在 *.editorconfig* 檔案中設為 **none** 的規則不會對清理有影響，但可透過 [快速動作與重構] 功能表另外套用。

## <a name="see-also"></a>另請參閱

- [快速動作](../ide/quick-actions.md)
- [EditorConfig 的 .NET 編碼慣例設定](../ide/editorconfig-code-style-settings-reference.md)
- [編輯器行為 (Visual Studio for Mac)](/visualstudio/mac/editor-behavior)