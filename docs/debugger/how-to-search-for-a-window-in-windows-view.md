---
title: 如何-在 Windows View 中搜尋視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb5fb871ebf03595c0baca0336e8449fe39029f3
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349233"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>如何：在視窗檢視中搜尋視窗
您可以使用控制項的控制碼、標題、類別，或其標題和類別的組合做為搜尋準則，在 Windows view 中搜尋特定視窗。 您也可以指定搜尋的初始方向。 對話方塊中的欄位會在視窗樹狀結構中顯示所選取視窗的屬性。

 從展開到第二個層級的樹狀結構開始（桌面的所有視窗），讓您可以依類別名稱和標題識別桌面層級視窗。 一旦您選擇了桌面層級視窗，就可以展開該層級來尋找特定的子視窗。

### <a name="to-search-for-a-window-in-windows-view"></a>在 Windows view 中搜尋視窗

1. 因此排列的視窗，Spy + + [Windows 檢視](../debugger/windows-view.md) 視窗和 [目標] 視窗會顯示。

2. 從 [**搜尋**] 功能表中，選擇 [**尋找視窗]**。

    [[視窗搜尋] 對話方塊](../debugger/window-search-dialog-box.md)隨即開啟。

   > [!TIP]
   > 若要減少螢幕雜亂，請選取 [**隱藏 Spy** ] 選項。 此選項會隱藏主 Spy + + 視窗，而且只會在其他應用程式頂端看到 [**視窗搜尋**] 對話方塊。 當您按一下 **[確定]** 或 [**取消**] 時，或清除 [**隱藏 Spy + +** ] 選項時，就會還原 Spy + + 主視窗。

3. 將搜尋**工具**拖曳到目標視窗上。 當您拖曳工具時，[**視窗搜尋**] 對話方塊會顯示所選視窗的詳細資料。

   - 或 -

     如果您知道您想要的視窗控制碼（例如，從偵錯工具），您可以在 [**控制碼**] 方塊中輸入它。

   - 或 -

     如果您知道所需視窗的標題和/或類別，可以在 [**標題**] 和 [**類別**] 文字方塊中輸入它們，並清除 [**控制碼**] 文字方塊。

4. 針對搜尋的初始方向，選擇 [**向上**] 或 [**向下**]。

5. 按一下 [確定]。

    如果找到相符的視窗，則會在[Windows View](../debugger/windows-view.md)視窗中反白顯示。