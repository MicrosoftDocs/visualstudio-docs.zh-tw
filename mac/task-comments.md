---
title: "工作註解"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 973e7b627a7b5c121ff388874577fe59c45529d7
ms.contentlocale: zh-tw
ms.lasthandoff: 08/11/2017

---

# <a name="task-comments"></a>工作註解

撰寫程式碼時，標準做法是明確註解未完成或有問題的程式碼，或使用警告進行快速因應措施。 雖然個人化權杖可以定義於 [Visual Studio] > [喜好設定] > [環境] > [工作] 下方，但是 Visual Studio for Mac 所提供的預設訊號權杖是 TODO、HACK、FIXME 和 UNDONE，如下所示：

 ![工作清單喜好設定](media/source-editor-image10.png)

若要新增工作註解，請新增包含工作關鍵字的註解。 例如: 

```
//TODO: Finish this for all properties.
```

Visual Studio for Mac 透過在 [工作清單] 板中反白顯示這些標記來注意它們，而此板的顯示方式是巡覽至 [檢視] > [板] > [工作]：

![工作清單板](media/source-editor-image11.png)
