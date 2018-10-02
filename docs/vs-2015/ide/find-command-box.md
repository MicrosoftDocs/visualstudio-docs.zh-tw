---
title: 尋找/命令方塊 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22ced396f8a18cf2a665ed7a1ba1016b16e44c8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487707"
---
# <a name="findcommand-box"></a>尋找/命令方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[尋找 / 命令方塊](https://docs.microsoft.com/visualstudio/ide/find-command-box)。  
  
您可以從 [尋找/命令] 方塊中搜尋文字，並執行 Visual Studio 命令。 [尋找/命令] 方塊仍然是工具列控制項，但不再預設為可見。 您可以選擇 [標準] 工具列上的 [新增或移除按鈕]，然後選擇 [尋找]，以顯示 [尋找/命令] 方塊。  
  
 若要執行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 命令，請在它前面加上大於 (>) 符號。  
  
 [尋找/命令] 方塊會保留輸入的最後 20 個項目，並以下拉式清單予以顯示。 您可以選擇方向鍵來巡覽清單。  
  
 ![尋找&#47;命令方塊](../ide/media/findcommandbox.png "FindCommandBox")  
尋找/命令方塊  
  
## <a name="searching-for-text"></a>搜尋文字  
 如果您在 [尋找/命令] 方塊中指定文字，然後選擇 ENTER 鍵，則 Visual Studio 預設會使用 [檔案中尋找] 對話方塊中所指定的選項來搜尋目前文件或工具視窗。 如需詳細資訊，請參閱 [Finding and Replacing Text](../ide/finding-and-replacing-text.md)。  
  
## <a name="entering-commands"></a>輸入命令  
 若要使用 [尋找/命令] 方塊來發出單一 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 命令或別名，而不是搜尋文字，請輸入 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 命令，並在前面加上大於 (>) 符號。 例如:   
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 或者，您也可以使用 [命令] 視窗輸入並執行單一或多個命令。 某些命令或別名可以單獨輸入並執行；有些命令或別名的語法則需要有引數。 如需含引數的命令清單，請參閱 [Visual Studio 命令](../ide/reference/visual-studio-commands.md)。  
  
## <a name="escape-characters"></a>逸出字元  
 命令列中的插入號 (^) 字元表示緊接著的字元會解譯為常值字元，而不是控制字元。 這可用來在參數或參數的值中嵌入一般引號 (")、空格、前置斜線、插入號或任何其他常值字元，但參數名稱除外。 例如，套用至物件的  
  
```  
>Edit.Find ^^t /regex  
```  
  
 無論插入號位於引號內部或外部，功能都相同。 如果插入號是該程式行的最後一個字元，則會將其忽略。  
  
## <a name="see-also"></a>另請參閱  
 [命令視窗](../ide/reference/command-window.md)   
 [尋找和取代文字](../ide/finding-and-replacing-text.md)



