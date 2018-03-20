---
title: "工作註解"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 674bae5b22c5b9ecc5d6fda4a9a4e30e4fcd1660
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="task-comments"></a>工作註解

撰寫程式碼時，標準做法是明確註解未完成或有問題的程式碼，或使用警告進行快速因應措施。 Visual Studio for Mac 所提供的預設訊號權杖是 TODO、HACK、FIXME 和 UNDONE。 個人化的權杖可在 [Visual Studio] > [喜好設定] > [環境] > [工作] 下定義，如下圖所示：

 ![工作清單喜好設定](media/source-editor-image10.png)

若要新增工作註解，請新增包含工作關鍵字的註解。 例如: 

```
//TODO: Finish this for all properties.
```

Visual Studio for Mac 透過在 [工作清單] 板中反白顯示這些標記來注意它們，而此板的顯示方式是巡覽至 [檢視] > [板] > [工作]：

![工作清單板](media/source-editor-image11.png)