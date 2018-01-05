---
title: "同步處理類型和檔案名稱-重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48172dd7-24a5-4884-8a73-f92497ad6a0d
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.workload: dotnet
ms.openlocfilehash: 2ec97bfc67735af08e80d7b6e8e67080d5b9af6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-c"></a>同步處理檔案名稱，或要在 C# 中的類型的檔案名稱的類型 #

<!-- VERSIONLESS -->
**這項功能是可在 Visual Studio 2017 及更新版本。此外，.NET 標準的專案是不尚未支援這項重構。**

**項目：**可讓您重新命名以符合檔案名稱、 類型或重新命名的檔名以符合它所包含的類型。

**當：**已重新命名檔案或類型，與您尚未尚未更新對應的檔案或要比對類型。 

**原因：**置於不同的名稱或反之亦然，很難找到您要尋找的檔案類型。  重新命名類型或檔名，程式碼變得更容易閱讀和您更輕鬆地瀏覽。

**如何：**

1. 反白顯示，或將文字指標放置要同步處理的型別名稱：

   ![反白顯示的程式碼](media/synctype_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**要重新命名檔案*TypeName*.cs**從預覽視窗快顯視窗，其中*TypeName*是您所選取的類型名稱。
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**重新命名類型_Filename_** 從預覽視窗快顯視窗，其中*Filename*是目前檔案的名稱。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**要重新命名檔案*TypeName*.cs**從預覽視窗快顯視窗，其中*TypeName*是您所選取的類型名稱。
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**重新命名類型_Filename_** 從預覽視窗快顯視窗，其中*檔名*是目前檔案的名稱。

   將立即重新命名類型或檔案。  在下列範例中，檔案**MyClass.cs**已重新命名為**MyNewClass.cs**要比對的型別名稱。

   ![Inline 結果](media/synctype_result.png)

## <a name="see-also"></a>請參閱  
[重構 (C#)](../refactoring-csharp.md)
