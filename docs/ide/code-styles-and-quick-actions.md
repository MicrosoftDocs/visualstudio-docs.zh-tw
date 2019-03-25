---
title: 程式碼樣式喜好設定
ms.date: 03/12/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: a7a478e8d3575e70a11ec776d59337ae93e7a677
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "57873356"
---
# <a name="code-style-preferences"></a>程式碼樣式喜好設定

從 [工具] 功能表中開啟 [選項] 對話方塊，以設定 C# 和 Visual Basic 專案的程式碼樣式喜好設定。 在 [選項] 對話方塊中，選取 [文字編輯器] > [C#] 或 [Basic] > [程式碼樣式] > [一般]。 清單中的每個項目會在選取時顯示個別的喜好設定預覽：

![程式碼樣式選項](media/code-style-quick-actions-dialog.png)

此視窗中所設定的選項適用於您的 Visual Studio 個人化帳戶，而且不會與特定專案或程式碼基底建立關聯。 此外，它們不會在建置階段強制執行，包含於持續整合 (CI) 組建中。 如果您想要將程式碼樣式喜好設定與您的專案建立關聯，並在建置期間強制執行樣式，請在 [.editorconfig 檔案](#editorconfig-files)中指定喜好設定。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的編輯器行為](/visualstudio/mac/editor-behavior)。

## <a name="preference-and-severity"></a>喜好設定和嚴重性

對於各個項目，您可以使用每一行的下拉式清單來設定 [喜好設定] 和 [嚴重性] 的值。 [嚴重性] 可設定為 [無]、[建議]、[警告] 或 [錯誤]。 如果您想要針對程式碼樣式啟用[快速動作](../ide/quick-actions.md)，請務必將 [嚴重性] 設定為 [無] 以外的值。 當使用非慣用樣式時，會出現**快速動作**燈泡![燈泡](media/light-bulb-dropdown.png)、錯誤燈泡![錯誤燈泡](media/error-bulb.png)或螺絲起子![螺絲起子](media/screwdriver.png)圖示，而您可以選擇 [快速動作] 清單上的選項，以自動將程式碼重寫成慣用的樣式。

## <a name="editorconfig-files"></a>EditorConfig 檔案

您也可以將 [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) 檔案新增至專案，來指定適用於 .NET 的程式碼樣式設定。 這些檔案都會與程式碼基底 (而非 Visual Studio 個人化帳戶) 建立關聯。 EditorConfig 檔案中設定的優先權高於 [選項] 對話方塊中選取的選項。 當您想要針對存放庫或專案的所有參與者強制執行編碼樣式時，請使用 EditorConfig 檔案。

## <a name="format-document-command"></a>將文件格式化命令

您可以設定 **Format Document** 命令 ([編輯] > [進階] > [格式化文件]) 以對檔案執行額外的程式碼清理，例如移除及排序 Using，或套用程式碼樣式喜好設定。 您可在 [[格式化] 選項頁面](reference/options-text-editor-csharp-formatting.md#format-document-settings)定義您希望**將文件格式化**套用哪些設定。

程式碼清理會遵循在 *.editorconfig* 檔案中進行的設定，若缺少該規則會檔案，則遵循 [工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] 或 [格式化] 中的設定。

當您第一次在 Visual Studio 中觸發 **Format Document** 命令時，黃色的資訊列會提示您進行程式碼清理設定。

> [!TIP]
> 若規則的嚴重性為 [無]，就不會參與程式碼清理，但可透過 [快速動作與重構] 功能表個別套用。

## <a name="see-also"></a>另請參閱

- [快速動作](../ide/quick-actions.md)
- [EditorConfig 的 .NET 編碼慣例設定](../ide/editorconfig-code-style-settings-reference.md)
- [編輯器行為 (Visual Studio for Mac)](/visualstudio/mac/editor-behavior)