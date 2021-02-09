---
title: 如何：匯出著色器
description: 瞭解如何使用著色器設計工具匯出有向圖形著色器語言著色器，讓您可以在應用程式中使用它。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f4abcdf5648031be9b76ba3f25e0a8f33d4efba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930963"
---
# <a name="how-to-export-a-shader"></a>如何：匯出著色器

本文將示範如何使用 [著色器設計工具] 匯出您可以在應用程式中使用的「有向圖著色器語言」(DGSL) 著色器。

## <a name="export-a-shader"></a>匯出著色器

當您使用著色器設計工具建立著色器之後，在您用於應用程式之前，必須以圖形 API 了解的格式將其匯出。 您可以根據不同的需求以不同的方式匯出著色器。

1. 在 Visual Studio 中，開啟 **視覺著色器圖形 (.dgsl)** 檔案。

     如果您沒有 **視覺著色器圖形 ( dgsl)** 檔案開啟，請依照 how [to：建立基本色彩著色器](../designers/how-to-create-a-basic-color-shader.md)中所述建立一個檔案。

2. 在 [著色器設計工具] 工具列上，選擇 [進階] > [匯出] > [匯出成]。 [匯出著色器] 對話方塊隨即出現。

3. 在 [存檔類型] 下拉式清單中，選擇您想要匯出的格式。

     以下是您可以選擇的格式︰

     **HLSL 像素著色器 (\*.hlsl)** 將著色器匯出為高階著色器語言 (HLSL) 原始程式碼。 此選項可讓您以後還能修改著色器，即使部署在應用程式之後也行。 這可讓您根據使用者的問題，更輕鬆地偵錯和修補程式，但也更容易讓使用者以不必要的方法修改您的著色器，例如在競爭遊戲中取得不公平的優勢。 也可能會增加載入著色器的時間。

     **編譯的像素著色器 (\*.cso)** 將著色器匯出為 HLSL 位元組程式碼。 此選項可讓您以後還能修改著色器，即使部署在應用程式之後也行。 這可讓您根據使用者的問題，更輕鬆地偵錯和修補程式，但因為是預先編譯的著色器，所以當應用程式載入著色器時，不會產生額外的執行階段負荷時間。 技術熟練的使用者仍可以不必要的方式修改著色器，但要將著色器編譯成此格式顯然更加困難。

     **C++ 標頭 (\*.h)** 將著色器匯出為 C-Style 標頭，其定義包含 HLSL 位元組程式碼的位元組陣列。 此選項會讓您在根據使用者問題來偵錯和修補程式時更加費時，因為必須重新編譯應用程式，才能測試修正。 不過，這個選項可讓著色器在應用程式部署之後就難以 (但無法杜絕) 修改，對想以不必要的方式修改著色器的使用者而言難度最高。

4. 在 [檔案名稱] 下拉式方塊中，為匯出的著色器指定名稱，然後選擇 [儲存] 按鈕。

## <a name="see-also"></a>另請參閱

- [如何：建立基本色彩著色器](../designers/how-to-create-a-basic-color-shader.md)
- [著色器設計工具](../designers/shader-designer.md)
