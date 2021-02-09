---
title: 使用率檢視 | Microsoft Docs
description: 瞭解 [使用率] 視圖會顯示目前進程所使用的 CPU、GPU 和其他系統資源的相關資訊。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 52dd5611e5a05de4bdb2d765bbdd2860e54f767e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885894"
---
# <a name="utilization-view"></a>使用率檢視
[使用率檢視] 顯示目前處理序使用的 CPU、GPU 和其他系統資源的相關資訊 (選擇 [分析] > [並行視覺化檢視] 來啟動並行視覺化檢視)。 顯示一段時間內在系統上執行的分析處理序、閒置處理序、系統處理序及其他處理序的平均核心使用率。 不會顯示在任何指定時間作用中的特定核心。 例如，如果兩個核心在指定期間各以 50% 的產量執行，然後此檢視會顯示共使用一個邏輯核心。 此檢視是將程式碼剖析時間分成數個區段而產生。 對於每個區段，圖形都會繪製在該間隔期間於邏輯核心上執行的處理序執行緒平均數目。

 ![CPU 使用率檢視](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")

 圖形顯示目標處理序、閒置處理序及系統處理序所使用的時間 (在 x 軸上) 與平均邏輯核心。 (閒置處理程序顯示閒置的核心。 系統進程是 Windows 中的進程，可代表其他進程執行工作。 ) 在系統帳戶上執行的其餘進程，以取得任何剩餘核心的使用率。

 邏輯核心數目會顯示在 y 軸上。 Windows 會將硬體中的同步多執行緒支援視為邏輯核心 (例如，超執行緒技術)。 因此，在每個核心支援兩個硬體執行緒的四核心處理器系統上，會顯示為 8 個邏輯核心系統。 這也適用於核心檢視。 如需詳細資訊，請參閱 [核心觀點](../profiling/cores-view.md)。

 GPU 活動圖會顯示在一段時間內處於使用中的 DirectX 引擎數。  如果引擎正在處理 DMA 封包，即為使用中。  該圖不會顯示特定的 DirectX 引擎 (例如，3D 引擎、視訊引擎及其他引擎)。

## <a name="purpose"></a>目的
 當您使用並行視覺化檢視時，建議您使用 [使用率檢視] 當成效能調查的起始點。 因為可提供一段時間內應用程式中的並行程度概觀，所以您可用來快速找出需要效能調整或平行處理的區域。

 如果您對效能調整感興趣，則可能會嘗試找出不符合您期望的行為。 您可能也會尋找邏輯 CPU 核心使用率低的區域和原因。 您可能也會尋找 CPU 和 GPU 之間的使用量模式。

 如果您對平行處理應用程式感興趣，則可能會尋找執行的 CPU-bound 區域或您尚未使用 CPU 的區域。

 CPU-bound 區域為綠色。 如果為序列應用程式，圖形會顯示正在使用一個核心。

 未使用 CPU 的區域為灰色。 這些可能代表當時應用程式處於閒置或在執行封鎖 I/O，藉機與其他 CPU-bound 工作重疊，進行平行處理原則。

 當您找到感興趣的行為時，您可加以選取來放大該區域。 在您放大之後，可以切換至 [執行緒] 檢視或[核心] 檢視，查看更詳細的分析。

 如果您使用 C++ AMP 或 DirectX 來使用 GPU，您可能會想要識別使用中的 GPU 引擎數或意外閒置 GPU 的區域。

## <a name="zoom"></a>Zoom
 若要放大 CPU 使用率圖形或 GPU 活動圖，請選取一個區段或使用圖形上方的 [縮放] 滑桿工具。 當您切換至其他檢視時，縮放設定會保持不變。 若要再次縮小，請使用 [縮放] 滑桿工具。 您也可以使用 **Ctrl** + **滾輪** 來縮放。

## <a name="see-also"></a>另請參閱
- [並行視覺化檢視](../profiling/concurrency-visualizer.md)
- [核心觀點](../profiling/cores-view.md)