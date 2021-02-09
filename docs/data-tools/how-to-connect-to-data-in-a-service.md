---
title: 如何：連接至服務中的資料
description: 執行資料來源設定向導，並在 [選擇資料來源類型] 頁面上選取 [服務]，將您的應用程式連接到從服務傳回的資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: d8e3692f376a502a2cd924fa9604eddab445333f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858757"
---
# <a name="how-to-connect-to-data-in-a-service"></a>如何：連線至服務中的資料

您可以執行 [[資料來源設定向導](../data-tools/media/data-source-configuration-wizard.png)]，然後在 [**選擇資料來源類型**] 頁面上選取 [**服務**]，將應用程式連接到從服務傳回的資料。

完成嚮導之後，服務參考即會加入至您的專案，並且可立即在 [ [資料來源] 視窗](add-new-data-sources.md#data-sources-window)中使用。

> [!NOTE]
> [資料來源] 視窗中所顯示的項目，取決於服務所傳回的資訊。 部分服務所提供的資訊可能不足，無法供 [資料來源組態精靈] 建立可繫結的物件。 例如，如果服務傳回不具類型的資料集，則完成嚮導時，[ **資料來源** ] 視窗中不會出現任何專案。 這是因為不具類型的資料集不提供架構，所以 wizard 沒有足夠的資訊來建立資料來源。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>將您的應用程式連線至服務

1. 在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。

2. 在 [**選擇資料來源類型**] 頁面上選取 [**服務**]，然後按 **[下一步]**。

3. 輸入您想要使用之服務的位址，或按一下 [ **探索** ] 以找出目前解決方案中的服務，然後按一下 [ **移至**]。

4. （選擇性）您可以輸入新的 **命名空間** 來取代預設值。

    > [!NOTE]
    > 按一下 [ **Advanced** ] 以開啟 [ [設定服務參考] 對話方塊](../data-tools/configure-service-reference-dialog-box.md)。

5. 按一下 **[確定]** ，將服務參考加入至您的專案。

6. 按一下 [完成] 。

     資料來源隨即新增至 [資料來源] 視窗。

## <a name="next-steps"></a>下一步

若要將功能加入至您的應用程式，請在 [ **資料來源** ] 視窗中選取專案，然後將它拖曳到表單上，以建立繫結控制項。 如需詳細資訊，請參閱 [將控制項系結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
