---
title: "專案設計工具、建置事件頁面 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c701adc4da2f59505699a02f1b4ccc304841f3ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="build-events-page-project-designer-c"></a>專案設計工具、建置事件 (C#)
使用 [專案設計工具] 的 [建置事件] 頁面，以指定組建組態指示。 您也可以指定執行任何建置後事件的條件。 如需詳細資訊，請參閱[如何：指定建置事件 (C#)](../../ide/how-to-specify-build-events-csharp.md) 和[如何：指定建置事件 (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **組態**  
 無法在此頁面中編輯這個控制項。 如需此控制項的描述，請參閱[專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)。  
  
 **平台**  
 在這個頁面上無法編輯此控制項。 如需此控制項的描述，請參閱[專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)。  
  
 **建置前事件命令列**  
 指定要在建置開始前執行的任何命令。 若要鍵入長命令，請按一下 [建置前進行編輯] 顯示[建置前事件/建置後事件命令列對話方塊](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。  
  
> [!NOTE]
>  如果專案是最新狀態，而且未觸發任何建置，則建置前事件不會執行。  
  
 **建置後事件命令列**  
 指定要在建置結束後執行的任何命令。 若要鍵入長命令，請按一下 [建置後進行編輯] 顯示 [建置前事件/建置後事件命令列] 對話方塊。  
  
> [!NOTE]
>  在執行 .bat 檔案的所有建置命令前方，加入 `call` 陳述式。 例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
 **執行建置後事件**  
 指定要執行建置後事件的下列條件，如下表所示。  
  
|選項|結果|  
|------------|------------|  
|**永遠**|不論建置是否成功，都會執行建置後事件。|  
|**建置成功時**|如果建置成功，則會執行建置後事件。 因此，即使專案是最新狀態，但只要建置成功，就會執行事件。|  
|**當組建更新專案輸出時**|只有在編譯器的輸出檔 (.exe 或 .dll) 與先前的編譯器輸出檔不同時，才會執行建置後事件。 因此，如果專案是最新狀態，就不會執行建置後事件。|  
  
## <a name="see-also"></a>另請參閱  
 [如何：指定建置事件 (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [如何：指定建置事件 (C#)](../../ide/how-to-specify-build-events-csharp.md)   
 [專案屬性參考](../../ide/reference/project-properties-reference.md)   
 [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)