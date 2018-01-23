---
title: "Visual Studio 程式碼樣式喜好設定 | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload: multiple
ms.openlocfilehash: 741df95afdd7c7e8b6f0ba2de75c1465cd35cc97
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="code-style-preferences"></a>程式碼樣式喜好設定

從 [工具] 功能表中開啟 [選項] 對話方塊，以設定 C# 和 Visual Basic 專案的程式碼樣式喜好設定。 選取 [文字編輯器] > [C#] 或 [Basic] > [程式碼樣式] > [一般]。 在此視窗中設定的選項適用於本機電腦。 清單中的每個項目會在選取時顯示喜好設定的預覽，如下所示。

![程式碼樣式選項](media/code-style-quick-actions-dialog.png)

對於每個項目，您可以使用每一列上的下拉式清單來設定 [喜好設定] 和 [嚴重性] 的值。 [嚴重性] 可設定為 [無]、[建議]、[警告] 或 [錯誤]。 如果您想要針對程式碼樣式啟用[快速動作](../ide/quick-actions.md)，請務必將 [嚴重性] 設定為 [無] 以外的值。 當使用非慣用樣式時，會出現快速動作燈泡圖示 ![小燈泡圖示](media/vs2015_lightbulbsmall.png)，且您可以選擇快速動作清單上的選項，以便將程式碼重新撰寫成慣用的樣式。

您也可以使用 [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) 檔案管理 .NET 程式碼樣式設定。 在此情況下，EditorConfig 檔案中設定的優先權高於 [選項] 對話方塊中所選取的選項。 您可以使用 EditorConfig 檔案強制執行並設定整個存放庫或專案的程式碼撰寫樣式。

## <a name="see-also"></a>另請參閱

[快速動作](../ide/quick-actions.md)  
[EditorConfig 的 .NET 編碼慣例設定](../ide/editorconfig-code-style-settings-reference.md)