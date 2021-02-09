---
title: 圖形診斷範例 |Microsoft Docs
description: 請參閱如何使用 Visual Studio 圖形診斷，以 DirectX 應用程式中的呈現問題的範例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07ddb9648c385346b7ff2cab2c082c5249317a3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879198"
---
# <a name="graphics-diagnostics-examples"></a>圖形診斷範例
這些範例示範如何使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 圖形診斷，偵錯 DirectX 應用程式中的呈現問題。

## <a name="capturing-graphics-information"></a>擷取圖形資訊
 您需要先從執行中的應用程式擷取圖形資訊，才能使用圖形診斷，診斷應用程式中的呈現問題。 您可以從在本機執行的應用程式，或是從在遠端電腦或其他裝置上執行的應用程式，擷取圖形資訊。 這些逐步解說示範如何手動或透過程式設計方式，從應用程式擷取圖形資訊：

- [逐步解說：擷取圖形資訊](walkthrough-capturing-graphics-information.md)

- [逐步解說：以程式設計方式擷取圖形資訊](walkthrough-capturing-graphics-information-programmatically.md)

## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>搭配 ARM 裝置使用圖形診斷
 您可以使用圖形診斷，透過遠端偵錯來偵錯 ARM 裝置上的 Direct3D 應用程式。 如需詳細資訊，請參閱 [如何：搭配使用圖形診斷與 ARM 裝置](graphics-diagnostics-examples.md)。

## <a name="playing-back-graphics-information"></a>播放圖形資訊
 在您從執行中應用程式擷取圖形資訊之後，就可以播放擷取的事件以診斷呈現問題。 若要播放，您可以使用開發電腦，也可以使用您所連接的遠端電腦或裝置。 如需詳細資訊，請參閱 [如何：變更圖形診斷播放電腦](how-to-change-the-graphics-diagnostics-playback-machine.md)。

## <a name="debugging-missing-objects"></a>偵錯遺漏物件
 遺漏物件是圖形開發人員最常遇到的呈現問題之一。 這類問題很難進行診斷，因為數個不同類型的錯誤可能會導致物件明顯消失。 遺漏物件的一般原因包括設定錯誤的裝置狀態、轉換物件的幾何時發生問題，或設定錯誤的圖形管線。

 這些情節示範如何使用圖形診斷，判斷物件遺漏原因，以及找出須對此負責的程式碼。

- [逐步解說：因裝置狀態而遺漏的物件](walkthrough-missing-objects-due-to-device-state.md)

- [逐步解說：因頂點著色而遺漏的物件](walkthrough-missing-objects-due-to-vertex-shading.md)

- [逐步解說：因管線設定錯誤而遺漏的物件](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)

## <a name="debugging-rendering-errors"></a>偵錯呈現錯誤
 圖形開發人員遇到的另一個常見問題是物件沒有正確外觀。 這類型的問題很難進行診斷，因為不正確外觀和造成此問題的原因的範圍很大，從十分明顯 (繫結錯誤的紋理) 到十分難以察覺 (著色器程式碼中的 Bug，或著色器之間的非預期互動)。 部分問題的原因可能是多個錯誤的合併。

 以下情節示範如何使用圖形診斷，追蹤由次要的著色器 Bug 造成的較容易察覺的呈現問題：

- [逐步解說：對因著色而產生的顯示錯誤進行偵錯](walkthrough-debugging-rendering-errors-due-to-shading.md)

## <a name="debugging-compute-shaders"></a>偵錯計算著色器
 您可以使用圖形診斷，偵錯產生錯誤結果的 DirectCompute 計算著色器核心。 您可以透過 DirectCompute，使用 GPU 的計算能力來平行執行大量資料項目的計算。 針對特定類型的問題，利用 GPU 的執行速度甚至可能比最佳化的 CPU 程式碼還要快數倍。 不過，傳統偵錯工具偵測不到在 GPU 上執行的程式碼。 偵錯這類程式碼需要特定的工具，而這些特定工具通常是廠商特有的，而且可能未與 Visual Studio 有良好的整合。 為了讓計算著色器在某個 GPU 範圍之間進行更一致的偵錯，圖形診斷會擷取 DirectCompute 分派事件 (除了 Direct3D 呈現事件之外)，讓您可以使用熟悉的工具來偵錯計算著色器程式碼中的問題。

 示範如何偵錯計算著色器中的 bug 所造成之模擬問題的案例，請參閱[逐步解說： 使用圖形診斷來偵錯計算著色器](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)。