---
title: 如何：連接至服務中的資料
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f3fd643ca29c5f5e4df20f244bc06b6bca04b9bd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930736"
---
# <a name="how-to-connect-to-data-in-a-service"></a>如何：連線至服務中的資料

連接您的應用程式，執行從服務傳回的資料[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)，然後選取**服務**上**選擇資料來源類型**頁面。

完成精靈的詳細資訊，服務參考加入至專案並立即提供[資料來源 視窗](add-new-data-sources.md#data-sources-window)。

> [!NOTE]
> [資料來源] 視窗中所顯示的項目，取決於服務所傳回的資訊。 部分服務所提供的資訊可能不足，無法供 [資料來源組態精靈] 建立可繫結的物件。 例如，如果服務傳回不具類型的資料集，顯示任何項目中**Zdroje dat**時完成精靈 的視窗。 這是因為不具類型資料集不會提供結構描述，所以精靈沒有足夠的資訊來建立資料來源。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>若要連接至服務的應用程式

1.  在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。

2.  選取 [**服務**上**選擇資料來源類型**頁面，然後再按一下**下一步]**。

3.  輸入您想要使用，或按一下 服務的位址**Discover**以在目前的方案中，尋找服務，然後按一下**移**。

4.  （選擇性） 您可以輸入新**命名空間**來取代預設的值。

    > [!NOTE]
    > 按一下 **進階**來開啟[設定服務參考對話方塊](../data-tools/configure-service-reference-dialog-box.md)。

5.  按一下 **確定**加入服務參考加入專案。

6.  按一下 [ **完成**]。

     資料來源隨即新增至 [資料來源] 視窗。

## <a name="next-steps"></a>後續步驟

若要將功能加入您的應用程式中，選取中的項目**Zdroje dat**視窗並將它拖曳至表單，以建立繫結的控制項。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)