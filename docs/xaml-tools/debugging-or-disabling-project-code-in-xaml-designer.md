---
title: 偵錯或停用 XAML 設計工具的專案程式碼
description: 瞭解如何在 XAML 設計工具中調試或停用專案程式碼，包括如何在 Visual Studio 的另一個實例中，對正在執行的專案程式碼進行偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: e03c33de81727c333db8f662232e669e37e78f59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921757"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>偵錯或停用 XAML 設計工具的專案程式碼

在許多情況下，當應用程式在設計工具中執行時，專案程式碼若是嘗試存取會傳回不同值或以不同方式運作的屬性或方法，就可能造成「XAML 設計工具」中發生未處理的例外狀況。 您可以偵錯 Visual Studio 另一個執行個體的專案程式碼來解決這些例外狀況；或暫時停用設計工具中的專案程式碼，防止例外狀況發生。

專案程式碼包括：

- 自訂控制項和使用者控制項

- 類別庫

- 值轉換器

- 標的為從專案程式碼產生之設計階段資料的繫結

當專案程式碼停用後，Visual Studio 會顯示預留位置。 例如，Visual Studio 會顯示不再提供資料之繫結的屬性名稱，或不再執行之控制項的預留位置。

![未處理的例外狀況對話方塊](media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>判斷專案程式碼是否會造成例外狀況

1. 在未處理的例外狀況對話方塊中，選擇 [按一下此處可重新載入設計工具]  連結。

2. 在功能表列上，選擇 [ **Debug**  >  **開始調試** 程式] 來建立和執行應用程式。

     如果應用程式順利建置並執行，則設計階段的例外狀況可能是由在設計工具中執行的專案程式碼所造成。

## <a name="to-debug-project-code-running-in-the-designer"></a>偵錯在設計工具中執行的專案程式碼

1. 在未處理的例外狀況對話方塊中，選擇 [按一下此處可停用執行中的專案程式碼並重新載入設計工具]  連結。

2. 在 [Windows 工作管理員] 中，選擇 [結束工作]  按鈕關閉 Visual Studio XAML 設計工具目前執行的所有執行個體。

     ![TaskManager 中的 XAML 設計工具執行個體](media/xaml_taskmanager.png)

3. 在 Visual Studio 中，開啟包含要偵錯之程式碼或控制項的 XAML 頁面。

4. 開啟 Visual Studio 的新執行個體，然後開啟您專案的第二個執行個體。

5. 設定專案程式碼的中斷點。

6. 在 Visual Studio 的新實例的功能表列上，選擇 [ **Debug**  >  **附加至進程**]。

7. 在 [附加至處理序]  對話方塊的 [可使用的處理序]  清單中，選擇 [XDesProc.exe] ，然後選擇 [附加]  按鈕。

     ![XAML 設計工具處理序](media/xaml_attach.png)

     這是 Visual Studio 第一個執行個體的 XAML 設計工具處理序。

8. 在 Visual Studio 的第一個實例的功能表列上，選擇 [ **Debug**  >  **開始調試** 程式]。

     您現在可以進入正在設計工具中執行的程式碼。

## <a name="to-disable-project-code-in-the-designer"></a>停用設計工具中的專案程式碼

- 在未處理的例外狀況對話方塊中，選擇 [按一下此處可停用執行中的專案程式碼並重新載入設計工具]  連結。

- 或者，在 XAML 設計工具的工具列上選擇 [停用專案程式碼] 按鈕。

     ![[停用專案程式碼] 按鈕](media/xaml_disablecode.png)

     您可以再次切換按鈕重新啟用專案程式碼。

    > [!NOTE]
    > 至於以 ARM 或 X64 處理器為目標的專案，Visual Studio 無法在設計工具中執行專案程式碼，所以停用設計工具中的 [停用專案程式碼]  按鈕。

- 無論哪個選項都會導致重新載入設計工具，然後停用所有相關聯專案的程式碼。

    > [!NOTE]
    > 停用專案程式碼會導致設計階段資料遺失。 另一個方法是偵錯在設計工具中執行的程式碼。

## <a name="control-display-options"></a>控制項顯示選項

> [!NOTE]
> **控制項顯示選項** 僅適用於以 Windows 10 Fall Creators Update (組建 16299) 或更新版本為目標的通用 Windows 平台應用程式。 Visual Studio 2017 15.9 或更新版本中提供了 **控制項顯示選項** 功能。

在 XAML 設計工具中，您可以將控制項顯示選項變更為僅顯示來自 Windows SDK 的平台控制項。 這可以提高 XAML 設計工具的可靠性。

若要變更控制項顯示選項，請按一下 [設計工具] 視窗左下角的圖示，然後選取 [控制項顯示選項] 下的選項：

![控制項顯示選項](media/control_display_options.png)

當您選取 [僅顯示平台控制項] 時，來自 SDK、客戶使用者控制項等的所有自訂控制項都將無法完全呈現。 相反地，它們會被後援控制項取代，以示範控制項的大小與位置。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 與 Blend for Visual Studio 中設計 XAML](designing-xaml-in-visual-studio.md)
