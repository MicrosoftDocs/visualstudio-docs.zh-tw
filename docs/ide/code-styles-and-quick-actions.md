---
title: Visual Studio 程式碼樣式喜好設定
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 6dd046fa8a01cde7abdc33484da3ff8227eda966
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
ms.locfileid: "34063680"
---
# <a name="code-style-preferences"></a>程式碼樣式喜好設定

從 [工具] 功能表中開啟 [選項] 對話方塊，以設定 C# 和 Visual Basic 專案的程式碼樣式喜好設定。 選取 [文字編輯器] > [C#] 或 [Basic] > [程式碼樣式] > [一般]。 在此視窗中設定的選項適用於本機電腦。

清單中的每個項目會在選取時顯示個別的喜好設定預覽：

![程式碼樣式選項](media/code-style-quick-actions-dialog.png)

## <a name="preference-and-severity"></a>喜好設定和嚴重性

對於各個項目，您可以使用每一行的下拉式清單來設定 [喜好設定] 和 [嚴重性] 的值。 [嚴重性] 可設定為 [無]、[建議]、[警告] 或 [錯誤]。 如果您想要針對程式碼樣式啟用[快速動作](../ide/quick-actions.md)，請務必將 [嚴重性] 設定為 [無] 以外的值。 當使用非慣用樣式時，會出現快速動作燈泡圖示 ![燈泡圖示](media/vs2015_lightbulbsmall.png)，而您可以選擇快速動作清單上的選項，以自動將程式碼重寫成慣用的樣式。

## <a name="editorconfig-files"></a>EditorConfig 檔案

您也可以使用 [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) 檔案管理 .NET 程式碼樣式設定。 EditorConfig 檔案中設定的優先權高於 [選項] 對話方塊中選取的選項。 您可以使用 EditorConfig 檔案強制執行並設定整個存放庫或專案的程式碼撰寫樣式。

## <a name="see-also"></a>另請參閱

- [快速動作](../ide/quick-actions.md)
- [EditorConfig 的 .NET 編碼慣例設定](../ide/editorconfig-code-style-settings-reference.md)