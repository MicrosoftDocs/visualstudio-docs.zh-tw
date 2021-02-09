---
title: 在 XAML UI 中將範例資料視覺化
titleSuffix: Blend for Visual Studio
description: 瞭解如何從頭開始產生範例資料，或從 Blend for Visual Studio 中的現有類別產生範例資料。
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7b8025f7212d28d2cfce482f67ef672a472993bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920114"
---
# <a name="display-data-in-blend-for-visual-studio"></a>在 Blend for Visual Studio 中顯示資料

您可以在自訂頁面的版面配置時於設計工具中檢視範例資料。 您可以從頭產生範例資料，或使用現有的類別。 您也可以連線到在執行應用程式時會出現於其中的「即時資料」。

> [!NOTE]
> Blend 中的 [ **資料** ] 面板僅支援以 .NET Framework 為目標的專案。 以 .NET Core 為目標的 UWP 專案或專案則不支援。

## <a name="generate-sample-data"></a>產生範例資料

若要產生範例資料，請開啟 XAML 文件。 在 [資料]  面板中，選擇 [建立範例資料] ![建立範例資料圖示](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) 按鈕，然後選擇 [新增範例資料] 。

在 [資料]  面板中定義資料結構，然後將它繫結至任何頁面上的 UI 項目。

![資料面板](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png)

如果您希望範例資料在執行應用程式時出現在頁面中，請選擇 [資料來源選項] ![資料來源選項圖示](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png)，然後選擇 [執行應用程式時啟用]。

![[執行應用程式時啟用] 功能表項目](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png)

**觀看短片︰** ![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [從頭建立範例資料](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2&preserve-view=true)。

## <a name="generate-sample-data-from-a-class"></a>從類別產生範例資料

如果您已經建立可描述資料結構的類別，可以從中產生範例資料。

若要從類別產生範例資料，請開啟 XAML 文件，然後在 [資料]  面板中，按一下 [建立範例資料] ![建立範例資料圖示](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) 按鈕，然後按一下 [從類別建立範例資料]。

**觀看短片︰** ![播放圖示](../designers/media/bldadminconsoleinitialconfigicon.PNG) [混合與 Blend 繫結的某些資料](https://www.youtube.com/watch?v=LSwPB6CAvjg)。

## <a name="see-also"></a>另請參閱

- [使用 Blend for Visual Studio 建立 UI](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)