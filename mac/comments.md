---
title: "註解"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: cb44dc755721f6095c9a07ad3e6fec1f6849e149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="comments"></a>註解

對程式碼進行偵錯或實驗時，暫時或長期註解程式碼區塊可能很有用。 

若要將整個程式碼區塊標記為註解：

* 選取程式碼，然後從操作功能表選取 [切換行註解]

或

* 在選取的程式碼上使用 `cmd + /` 按鍵繫結關係。

這些方法可用來註解和取消註解程式碼區段。 在 C# 檔案中，可以新增其他行註解層級，這可讓您註解和取消註解程式碼區域，同時仍保留實際註解： 

 ![多層級註解](media/source-editor-image8.png)

對於未來可能會與程式碼進行互動的開發人員，註解也可用來記錄程式碼。 這些通常是以多行註解的形式進行，而多行註解則使用下列方式新增在每個語言中：

**C#**

``` cs
/*
 This is a multi-line
 comment in C#
*/
```
**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```
