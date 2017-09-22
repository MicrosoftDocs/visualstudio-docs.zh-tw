---
title: "程式碼樣式及快速動作 | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: acc01617fffd7465cee01267482112aac5e352fc
ms.contentlocale: zh-tw
ms.lasthandoff: 03/27/2017

---

# <a name="code-styles-and-quick-actions"></a>程式碼樣式及快速動作
可以藉由開啟 [工具] > [選項] 視窗，然後選取 [文字編輯器] > [C# / Basic] > [程式碼樣式] > [一般] 為 C# 和 Visual Basic 專案設定程式碼樣式喜好設定。  在此視窗中設定的選項適用於本機電腦。  清單中的每個項目會在選取時顯示喜好設定的預覽，如下所示。

![程式碼樣式選項](media/code-style-quick-actions-dialog.png)

對於每個項目，您可以使用每一列上的下拉式清單設定 [喜好設定] 和 [嚴重性]。  可以將嚴重性設為 [無]、[建議]、[警告] 或 [錯誤]，Visual Studio 會適當地運作。  如果您想要使用[快速動作](quick-actions.md)搭配這些程式碼樣式，將程式碼自動重寫為慣用的樣式，請確定該設定已設為 [無] 以外的其他值，如此燈泡圖示 ![小燈泡圖示](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") 在使用非慣用的樣式時出現。  這些喜好設定便可以藉由當您的游標位於適當程式碼行時，按一下燈泡圖示或按 **Ctrl + .** 來套用。

您也可以使用 [EditorConfig](editorconfig-code-style-settings-reference.md) 檔案管理 .NET 程式碼樣式設定。  在此情況下，[選項] 視窗中選取的設定會是後援設定，EditorConfig 檔案則會優先。  您可以使用這個檔案強制執行並設定整個儲存機制或小組的程式碼撰寫樣式。

# <a name="see-also"></a>另請參閱
* [快速動作](quick-actions.md)
