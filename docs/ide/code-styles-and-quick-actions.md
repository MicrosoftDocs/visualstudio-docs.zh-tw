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
ms.openlocfilehash: 24470f4fdb1a75d6ebd2743b2ade72e6195842b4
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2017
---
# <a name="code-style-preferences"></a>程式碼樣式喜好設定

從 [工具] 功能表中開啟 [選項] 對話方塊，以設定 C# 和 Visual Basic 專案的程式碼樣式喜好設定。 選取 [文字編輯器]、[C#] 或 [基本]、[程式碼樣式]、[一般]。 在此視窗中設定的選項適用於本機電腦。 清單中的每個項目會在選取時顯示喜好設定的預覽，如下所示。

![程式碼樣式選項](media/code-style-quick-actions-dialog.png)

對於每個項目，您可以使用每一列上的下拉式清單設定 [喜好設定] 和 [嚴重性]。 可以將嚴重性設為 [無]、[建議]、[警告] 或 [錯誤]，Visual Studio 會適當地運作。 如果您想要使用[快速動作](quick-actions.md)搭配這些程式碼樣式，將程式碼自動重寫為慣用的樣式，請確定該設定已設為 [無] 以外的其他值，如此燈泡圖示 ![小燈泡圖示](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") 在使用非慣用的樣式時出現。 這些喜好設定便可以藉由當您的游標位於適當程式碼行時，按一下燈泡圖示或按 **Ctrl + .** 來套用 。

您也可以使用 [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) 檔案管理 .NET 程式碼樣式設定。 在此情況下，EditorConfig 檔案中設定的優先權高於 [選項] 對話方塊中所選取的選項。 您可以使用 EditorConfig 檔案強制執行並設定整個存放庫或專案的程式碼撰寫樣式。

## <a name="see-also"></a>請參閱

[快速動作](quick-actions.md)  
[EditorConfig 的 .NET 編碼慣例設定](../ide/editorconfig-code-style-settings-reference.md)