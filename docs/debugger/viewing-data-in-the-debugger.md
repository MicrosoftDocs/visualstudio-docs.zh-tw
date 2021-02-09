---
title: 在偵錯工具中建立資料的自訂視圖 |Microsoft Docs
description: 瞭解在 Visual Studio 偵錯工具中檢查和修改程式狀態的各種方式。 這些包括自動變數和監看式視窗、資料提示和視覺化檢視。
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d51821597c68a9b8e0c97e4cac3c7dc7ec2b8cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884347"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>在 Visual Studio 偵錯工具中建立資料的自訂資料檢視 (c #、Visual Basic、c + +) 

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]偵錯工具提供許多工具來檢查和修改程式的狀態。 這些工具大多數只能在中斷模式下運作。

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>在變數視窗和資料提示中建立資料的自訂視圖

 許多 [偵錯工具視窗](../debugger/debugger-windows.md)（例如 [自動變數] **和 [** **監看式]** 視窗）都可讓您檢查變數。 您可以自訂 c + + 類型、managed 物件和您自己的類型如何顯示在偵錯工具變數視窗和 [資料提示](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)中。 如需詳細資訊，請參閱 [建立 c + + 物件的自訂視圖](../debugger/create-custom-views-of-native-objects.md) ，以及 [建立受控物件的自訂視圖](../debugger/create-custom-views-of-managed-objects.md)。

## <a name="create-custom-visualizers"></a>建立自訂視覺化檢視

 視覺化程式可讓您以有意義的方式來查看物件或變數的內容。 在 Visual Studio 偵錯工具中，視覺化程式是指您可以使用放大鏡 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示") 圖示來開啟的不同視窗。 例如，HTML 視覺化程式會顯示 HTML 字串在瀏覽器中的解讀和顯示方式。 您可以從 [資料 **提示]、** [**監看** 式] 視窗、[自動 **變數**] 視窗和 [區域變數] 視窗存取視覺化檢視。 [ **快速** 監看式] 對話方塊也會提供視覺化。 如需詳細資訊，請參閱[建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)。

## <a name="see-also"></a>另請參閱

- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [命令視窗](../ide/reference/command-window.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
