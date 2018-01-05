---
title: "產生的建構函式的程式碼產生 (C#) |Microsoft 文件"
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
ms.openlocfilehash: 9ffa85d768939522935199edde6d0f19b3f2b7a2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-constructor-in-c"></a>在 C# 中產生的建構函式 #
**項目：**可讓您立即產生新的建構函式，在類別上的程式碼。 

**當：**您引入新的建構函式，若要正確地自動宣告，或修改現有的建構函式。 

**原因：**不過這項功能將它，以適當的參數自動產生，您可以再使用它，宣告建構函式。 此外，修改現有的建構函式，必須更新所有 callsite，除非您使用這項功能來自動更新。

**如何：**幾種方式來產生建構函式：
- [產生建構函式，並挑選成員](#pick)
- [從選取的欄位產生建構函式](#selection)
- [從新的使用方式產生建構函式](#usage)
- [將參數加入至現有的建構函式](#addparameter)
- [建立和初始化欄位/屬性從建構函式參數](#create)

## <a id = "pick"></a>產生建構函式，並挑選成員
1. 將游標放在類別中的任何空白一行：

   ![空白列中的資料指標](media/constructor1_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**產生建構函式...**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**產生建構函式...**從預覽視窗快顯視窗。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經存在於類別中的空白列，會出現在左邊界的圖示。

   ![產生建構函式預覽](media/constructor1_preview.png)

1. 會出現一個對話方塊，讓您可以挑選並選擇您想要做為建構函式參數，以及排列這些資料行 （使用向上和向下箭號） 哪些的成員。 按**確定**認可變更。
  
   ![選取成員 對話方塊](media/constructor1_dialog.png)

   >[!TIP] 
   >您可以檢查**加入 null 檢查，**核取方塊以自動產生建構函式參數的 null 檢查。

1. 建構函式將會建立與選取的參數指定的順序。
   ![產生建構函式的結果](media/constructor1_result.png)

## <a id="selection"></a>從選取的欄位產生建構函式
1. 反白顯示您想要讓您產生的建構函式中的成員：![反白顯示成員](media/constructor2_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**產生建構函式 'TypeName(...)'**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**產生建構函式 'TypeName(...)'**從預覽視窗快顯視窗。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經列中利用選取項目，會出現在左邊界的圖示。

     ![產生建構函式預覽](media/constructor2_preview.png)

1. 建構函式將會建立與選取的參數。
     ![產生建構函式的結果](media/constructor2_result.png)

## <a id="usage"></a>從新的使用方式產生建構函式
1. 將游標放在該行其中會有紅色曲線，表示您已使用建構函式不存在。

   ![反白顯示的程式碼](media/constructor_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**中的產生建構函式 '*TypeName*' * * 從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**中的產生建構函式 '*TypeName*' * * 從預覽視窗快顯視窗。
     * 將滑鼠停留在紅色波浪線，然後按一下 ![Lightbulb](media/bulb.png) 圖示會出現。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經存在於紅色曲線的線條，會出現在左邊界的圖示。

   ![產生建構函式預覽](media/constructor_preview.png)

   >[!TIP]
   >使用[**預覽變更**](../../ide/preview-changes.md)若要查看的所有變更都會在您的選取項目之前，[預覽] 視窗底部的連結。

1. 建構函式會自動建立的任何參數，從其使用方式推斷。

   ![產生建構函式的結果](media/constructor_result.png)

## <a id="selection"></a>將參數加入至現有的建構函式
1. 將參數加入至現有的物件具現化。

1. 將游標放在該行其中會有紅色曲線，表示您已使用建構函式不存在。
    
    ![產生建構函式的反白顯示](media/constructor4_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**將參數加入至 'TypeName(...)'**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**將參數加入至 'TypeName(...)'**從預覽視窗快顯視窗。
     * 將滑鼠停留在紅色波浪線，然後按一下 ![Lightbulb](media/bulb.png) 圖示會出現。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經存在於紅色曲線的線條，會出現在左邊界的圖示。

    ![產生建構函式預覽](media/constructor4_preview.png)

1. 參數會自動新增，以及從其使用方式推斷其類型。
   
   ![產生建構函式的結果](media/constructor4_result.png)

## <a id="create"></a>建立和初始化欄位/屬性從建構函式參數
1. 從現有的建構函式，加入參數：

   ![產生建構函式的反白顯示](media/constructor5_highlight.png)

1. 將您的游標新加入的參數。

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**建立和初始化的屬性 'YourProperty'**或**建立和初始化的欄位 'YourField'**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**建立和初始化的屬性 'YourProperty'**或**建立和初始化的欄位 'YourField'**從預覽視窗快顯視窗。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經列中利用加入的參數，會出現在左邊界的圖示。

   ![產生建構函式預覽](media/constructor5_preview.png)

1. 欄位/屬性將會建立並自動命名以符合您的型別。

   ![產生建構函式的結果](media/constructor5_result.png)
  
## <a name="see-also"></a>請參閱  
[程式碼產生 (C#)](../code-generation-csharp.md)  
[預覽變更](../../ide/preview-changes.md)