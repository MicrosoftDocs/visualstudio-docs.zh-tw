---
title: "產生的類別或類型-產生程式碼 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: csharp
ms.openlocfilehash: b6825be5447718e47f7145b0b3b16ec6d0ee076c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-class-or-type-in-c"></a>在 C# 中產生類別或類型 #
**項目：**可讓您立即產生類別或類型的程式碼。 

**當：**您引入新的類別或類型，而且想要正確地自動宣告。  

**原因：**您可以使用，不過這項功能將會產生類別，或自動輸入之前，先宣告類別或類型。 

**如何：**

1. 將游標放在該行其中會有紅色曲線，表示您已使用還不存在的類別。

   ![反白顯示的程式碼](media/class_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表並選取其中一個 [預覽] 視窗的快顯視窗中的選項。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表並選取其中一個 [預覽] 視窗的快顯視窗中的選項。
     * 將滑鼠停留在紅色波浪線，然後按一下 ![Lightbulb](media/bulb.png) 圖示會出現。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經存在於紅色曲線的線條，會出現在左邊界的圖示。

   ![產生類別預覽](media/class_preview.png)

   選取 | 說明
   --- | ---
   產生類別*TypeName*' 中新的檔案 | 建立名為類別*TypeName*中名為*TypeName*.cs/.vb
   產生類別*TypeName*' | 建立名為類別*TypeName*目前檔案中。
   產生巢狀的類別*TypeName*' | 建立名為類別*TypeName*巢狀方式置於目前的類別。
   產生新類型... | 所有您指定的屬性，會建立新的類別或結構。

   >[!TIP]
   >使用[**預覽變更**](../../ide/preview-changes.md)若要查看的所有變更都會在您的選取項目之前，[預覽] 視窗底部的連結。

1. 如果您選取**產生新的類型...**項目，對話方塊會隨即快顯，可讓您執行一些額外的動作。

   ![產生類型](media/class_newtype.png)

   選取 | 說明
   --- | ---
   存取 | 將類型設定為具有*預設*，*內部*或*公用*存取。
   類型 | 這可設定為*類別*或*結構*。
   名稱 | 無法變更，而且將會是您已輸入的名稱。
   專案 | 如果您的方案中有多個專案，您可以選擇您想要類別/結構存留。
   檔案名稱 | 您可以建立新的檔案，或將類型加入至現有的檔案。

1. 類別/結構會自動建立的建構函式從其使用方式推斷。

   ![產生類別的結果](media/class_result.png)

## <a name="see-also"></a>另請參閱  
[程式碼產生 (C#)](../code-generation-csharp.md)  
[預覽變更](../../ide/preview-changes.md)