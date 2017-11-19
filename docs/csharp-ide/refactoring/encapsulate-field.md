---
title: "封裝欄位-重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 39a9ed11-363f-4dda-af3b-0affe6db1d42
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: csharp
ms.openlocfilehash: f934d33d2c7bdc698b00305f3c86f904eae99e33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-a-field-in-c"></a>封裝 C# 中的欄位 #
**項目：**可讓您將欄位轉換成屬性，並更新所有使用該欄位，以使用新建立的屬性。

**當：**您想要將欄位移到屬性，並更新該欄位的所有參考。  

**原因：**您想要讓其他類別存取欄位，但不想要能夠直接存取這些類別。  透用包裝在屬性中的欄位，您可以撰寫程式碼來確認指派的值，例如。

**如何：**

1. 反白顯示，或將文字指標放置封裝欄位的名稱：

   ![反白顯示的程式碼](media/encapsulate_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl + R**，然後**Ctrl + E**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表並選取 **封裝欄位**預覽視窗快顯功能表項目。
   * **滑鼠**
     * 選取**編輯 > 重構 > 封裝欄位**。
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表並選取 **封裝欄位**預覽視窗快顯功能表項目。

   選取 | 說明
   --------- | -----------
   **封裝欄位 （並使用屬性）** | 封裝具有屬性的欄位，並更新使用產生的屬性欄位的所有使用方式
   **封裝欄位 （但仍使用欄位）** | 封裝具有屬性的欄位，但會讓所有的欄位的使用方式不變

   立即建立屬性和欄位的參考，將會更新，選取。

   > [!TIP]
   > 使用[**預覽變更**](../../ide/preview-changes.md)以查看結果將會認可之前, 的快顯視窗中的連結。

   ![封裝屬性結果](media/encapsulate_result.png)

## <a name="see-also"></a>另請參閱  
[重構 (C#)](../refactoring-csharp.md)  
[預覽變更](../../ide/preview-changes.md)