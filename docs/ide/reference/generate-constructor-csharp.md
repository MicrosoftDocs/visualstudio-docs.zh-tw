---
title: "產生建構函式 - 程式碼產生 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b6e73b3b012547e98934bbcd76d1ee2eb0f3324d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-constructor-in-c"></a>使用 C# 來產生建構函式 #
**功能：**讓您立即針對類別產生新建構函式的程式碼。 

**時機：**您引進新的建構函式並想要自動正確地宣告它，或是您修改現有的建構函式。 

**原因：**您可以在使用建構函式之前先宣告它，不過，此功能將可自動搭配正確的參數來產生建構函式。 此外，修改現有的建構函式將需要更新所有 callsite，除非您使用此功能來自動更新它們。

**做法：**有數種產生建構函式的方式：
- [產生建構函式並選取成員](#pick)
- [從選取的欄位產生建構函式](#selection)
- [從新的使用方式產生建構函式](#usage)
- [將參數新增至現有的建構函式](#addparameter)
- [從建構函式參數建立欄位/屬性並加以初始化](#create)

## <a id = "pick"></a> 產生建構函式並選取成員
1. 將游標放在類別中任何空白的一行：

   ![游標在空白行中](media/constructor1-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生建構函式]。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生建構函式]。
     * 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在類別中的空白行上，此圖示就會出現在左邊界上。

   ![「產生建構函式」預覽](media/constructor1-preview-cs.png)

1. 將會顯示一個對話方塊，可讓您挑選要用來作為建構函式參數的成員並加以排列 (使用向上和向下箭號)。 按 [確定] 以認可您的變更。
  
   ![[選取成員] 對話方塊](media/constructor1-dialog-cs.png)

   >[!TIP] 
   >您可以選取 [新增 null 檢查] 核取方塊，來自動為建構函式參數產生 null 檢查。

1. 系統將會使用所選參數以指定的順序建立建構函式。
   ![「產生建構函式」結果](media/constructor1-result-cs.png)

## <a id="selection"></a> 從選取的欄位產生建構函式
1. 醒目標示您想要包含在所產生建構函式中的成員：![醒目標示成員](media/constructor2-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生建構函式 'TypeName(...)']。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生建構函式 'TypeName(...)']。
     * 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有選取項目的行上，此圖示就會出現在左邊界上。

     ![「產生建構函式」預覽](media/constructor2-preview-cs.png)

1. 系統將會使用所選參數來建立建構函式。
     ![「產生建構函式」結果](media/constructor2-result-cs.png)

## <a id="usage"></a> 從新的使用方式產生建構函式
1. 將游標放在有紅色曲線的行上，該曲線代表您使用尚未存在的建構函式。

   ![醒目標示的程式碼](media/constructor-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [在 '*TypeName*' 中產生建構函式]。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [在 '*TypeName*' 中產生建構函式]。
     * 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-cs.png) 圖示。
     * 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

   ![「產生建構函式」預覽](media/constructor-preview-cs.png)

   >[!TIP]
   >請使用位於預覽視窗底部的 [[預覽變更](../../ide/preview-changes.md)] 連結，以在進行選取之前先查看將進行的所有變更。

1. 系統將會使用從建構函式使用方式推斷的任何參數來自動建立建構函式。

   ![「產生建構函式」結果](media/constructor-result-cs.png)

## <a id="addparameter"></a> 將參數新增至現有的建構函式
1. 將參數新增至現有的物件具現化。

1. 將游標放在有紅色曲線的行上，該曲線代表您使用尚未存在的建構函式。
    
    ![「產生建構函式」醒目標示](media/constructor4-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將參數新增至 'TypeName(...)']。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將參數新增至 'TypeName(...)']。
     * 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-cs.png) 圖示。
     * 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

    ![「產生建構函式」預覽](media/constructor4-preview-cs.png)

1. 系統將會使用從參數使用方式推斷的類型來自動新增參數。
   
   ![「產生建構函式」結果](media/constructor4-result-cs.png)

## <a id="create"></a> 從建構函式參數建立欄位/屬性並加以初始化
1. 從現有的建構函式，新增參數：

   ![「產生建構函式」醒目標示](media/constructor5-highlight-cs.png)

1. 將游標放在剛新增的參數內。

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [建立並初始化屬性 'YourProperty'] 或 [建立並初始化欄位 'YourField']。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [建立並初始化屬性 'YourProperty'] 或 [建立並初始化欄位 'YourField']。
     * 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有所新增參數的行上，此圖示就會顯示在左邊界上。

   ![「產生建構函式」預覽](media/constructor5-preview-cs.png)

1. 系統將會建立欄位/屬性並自動依據類型來命名。

   ![「產生建構函式」結果](media/constructor5-result-cs.png)

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)