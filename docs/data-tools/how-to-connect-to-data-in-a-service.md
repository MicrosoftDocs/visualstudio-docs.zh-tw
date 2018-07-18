---
title: 如何：連接至服務中的資料
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d6f90a99a387452500686af332edb1d112a88f82
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089114"
---
# <a name="how-to-connect-to-data-in-a-service"></a>如何： 連接到服務中的資料

連接您的應用程式，執行從服務傳回的資料[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)，然後選取**服務**上**選擇資料來源類型**頁面。

完成精靈的詳細資訊，服務參考加入至專案並立即提供[資料來源視窗](add-new-data-sources.md)。

> [!NOTE]
> 在出現的項目**Zdroje dat**視窗均依存於服務所傳回的資訊。 某些服務可能並未提供足夠的資訊，如**資料來源組態精靈**來建立可繫結的物件。 例如，如果服務傳回不具類型的資料集，顯示任何項目中**資料來源視窗**時正在完成精靈。 這是因為不具類型資料集不會提供結構描述，所以精靈沒有足夠的資訊來建立資料來源。

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

     若要新增資料來源**Zdroje dat**視窗。

## <a name="next-steps"></a>後續步驟

若要將功能加入您的應用程式中，選取中的項目**Zdroje dat**視窗並將它拖曳至表單，以建立繫結的控制項。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [在 Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)