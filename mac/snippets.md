---
title: "程式碼片段"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 1f2ee1d440ad1c7d8cd75ae9194c651f2fc16a41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="code-snippets"></a>程式碼片段 

程式碼片段通常稱為「程式碼範本」，適用於具效率的程式設計，因為它們允許插入和編輯預先撰寫的程式碼區塊。 使用程式碼片段可能特別方便於迅速新增常見模式，或甚至在您是開發人員但不確定語法時學習新的模式。 有針對 C#、F#、HTML、XML、Python 和 Razor 提供的範本。

本節說明如何在程式碼中建立、插入和使用程式碼片段。

## <a name="inserting-a-snippet"></a>插入程式碼片段

有一些不同的方式可以新增程式碼片段，而下面說明其中一部分：
 
* **定位點擴充** - 開始鍵入範本名稱，並從清單中選取它，然後按 **TAB TAB** 新增它：
 
  ![程式碼中的定位點擴充](media/source-editor-image13.png)

* **工具箱** - 使用工具箱板顯示所有程式碼片段的清單。 將任何範本從工具箱拖曳至原始程式碼中的正確位置：

 ![工具箱中的程式碼片段](media/source-editor-image14.png)

* **插入命令範本** - 目前未設定插入範本的預設按鍵繫結關係。 若要建立按鍵繫結關係，請瀏覽至 [Visual Studio] > [喜好設定] > [按鍵繫結關係]，並搜尋 `template`。 這允許將想要的按鍵繫結關係新增至 [編輯繫結] 欄位，然後按一下 [套用]：

 ![插入範本命令](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>建立新範本

雖然您可以使用和編輯多個各種語言的現有範本，但也可以新增範本，方法是巡覽至 [Visual Studio] > [喜好設定] > [文字編輯器] > [程式碼片段]：

![插入新範本](media/source-editor-image12.png)
