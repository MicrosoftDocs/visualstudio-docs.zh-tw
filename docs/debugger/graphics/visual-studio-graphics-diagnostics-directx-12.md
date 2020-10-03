---
title: Visual Studio 中的 DirectX 12 支援 |Microsoft Docs
description: 建議使用 DirectX 12 使用者，在 Windows 上使用 PIX 進行完整的圖形化偵錯工具
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671394"
---
# <a name="directx-12-support-in-visual-studio"></a>Visual Studio 中的 DirectX 12 支援

## <a name="directx-12-support"></a>DirectX 12 支援

Visual Studio 圖形診斷不支援 DirectX 12 遊戲。 如需完整的 DirectX 12 支援進行圖形化的偵錯工具，Visual Studio 建議 *Windows 上的 PIX*。 

Windows 上的 PIX 是具有遠端功能的效能微調和偵錯工具。 Windows 上的 PIX 提供七個符合圖形化調試需求的主要功能。 使用 GPU 捕獲來偵測並分析 Direct3D 12 圖形轉譯的效能。 瞭解遊戲使用計時捕捉所執行之所有 CPU 和 GPU 工作的效能和執行緒。 使用檔案 IO 捕獲找出您標題的磁片 IO 模式和套件配置中效率不佳的情況。

在 Windows 上按下您的圖形偵錯工具與 [**PIX**](https://aka.ms/PIXonWindows)。

[**下載 Windows 上的 PIX**](https://aka.ms/downloadPIX) 或 [**查看檔**。](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>Windows 上的 PIX

Windows 上的 PIX 有七種主要的操作模式：
1. 適用于偵錯工具和分析 Direct3D 12 圖形轉譯效能的**GPU 捕獲**。
2. **時間捕捉** 可瞭解您的遊戲所執行之所有 CPU 和 GPU 工作的效能和執行緒，以及追蹤 GPU 記憶體使用量。
3. 函式**摘要**會累積每個函式執行的時間長度，以及每個函式的呼叫頻率等相關資訊。
4. **Callgraph 會捕捉** 單一函式執行的追蹤。
5. **記憶體配置的捕獲** 可讓您深入瞭解您的遊戲所做的記憶體配置。
6. 檔案**IO 捕獲**可協助您找出標題磁片 IO 模式和套件配置的效率不佳。
7. 當遊戲正在執行時，**系統監視器**會顯示即時計數器資料。

您可以在這裡找到 Windows 上 PIX 的詳細影片簡介[ **here**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)
