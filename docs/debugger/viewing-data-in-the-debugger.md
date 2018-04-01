---
title: 在 偵錯工具中建立資料的自訂檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/27/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e8f008ba3cde911ed5c21f281d30fda2a77bf824
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>在 Visual Studio 偵錯工具中建立資料的自訂檢視
各種由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具所提供的工具，都可用來檢查和修改您的程式狀態。 這些工具大多數只能在中斷模式下運作。

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>建立自訂檢視的資料在變數視窗和資料提示方塊
 許多[偵錯工具視窗](../debugger/debugger-windows.md)，例如**自動變數**和**監看式**視窗可讓您在偵錯時檢查變數。 您可以自訂的原生型別與受管理的物件，在偵錯工具變數視窗中，然後在顯示[DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)。 這可以是很有幫助以顯示您在自己的應用程式中建立的類型。 如需詳細資訊，請參閱[建立原生物件的自訂檢視](../debugger/create-custom-views-of-native-objects.md)和[建立受管理物件的自訂檢視](../debugger/create-custom-views-of-dot-managed-objects.md)。
  
## <a name="create-custom-visualizers"></a>建立自訂的視覺化檢視  
 視覺化檢視可讓您檢視物件或變數的內容中有意義的方式。 在 Visual Studio 偵錯工具視覺化檢視是指您可以使用放大鏡圖示來開啟的不同 windows ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")。 例如，可以使用 HTML 視覺化工具來檢視 HTML 字串，如同在瀏覽器中解譯和顯示的字串一樣。 您可以從資料提示方塊、[監看式]  視窗、[自動變數]  視窗、[區域變數]  視窗或 [快速監看式]  對話方塊存取視覺化工具。 如需詳細資訊，請參閱[建立自訂的視覺化檢視](../debugger/create-custom-visualizers-of-data.md)。
  
## <a name="see-also"></a>請參閱  
 [偵錯工具基礎](../debugger/debugger-basics.md)   
 [命令視窗](../ide/reference/command-window.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)