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
ms.openlocfilehash: 3975d7f0bcfc9b80c944c892cde52f2b625e0bbf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-connect-to-data-in-a-service"></a>如何：連接至服務中的資料

您應用程式連接至服務執行所傳回的資料[資料來源組態精靈](../data-tools/media/data-source-configuration-wizard.png)，然後選取**服務**上**選擇資料來源類型**頁面。

完成精靈的詳細資訊，服務參考加入至專案並立即可用於[資料來源視窗](add-new-data-sources.md)。

> [!NOTE]
> 在出現的項目**資料來源**視窗會取決於服務所傳回的資訊。 某些服務可能會提供足夠的資訊如**資料來源組態精靈**來建立可繫結的物件。 例如，如果服務傳回不具類型的資料集，然後顯示任何項目中**資料來源視窗**完成精靈之後。 這是因為不具類型資料集不會提供結構描述，因此精靈並沒有足夠的資訊來建立資料來源。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>若要連接至服務應用程式

1.  在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。

2.  選取**服務**上**選擇資料來源類型**頁面，然後再按一下**下一步**。

3.  輸入您想要使用，或按一下服務的位址**探索**在目前方案中，找不到服務，然後按一下**移**。

4.  （選擇性） 新**命名空間**可以類型來取代預設值。

    > [!NOTE]
    > 按一下**進階**開啟[設定服務參考對話方塊](../data-tools/configure-service-reference-dialog-box.md)。

5.  按一下**確定**加入服務參考加入專案。

6.  按一下 [ **完成**]。

     資料來源加入至**資料來源**視窗。

## <a name="next-steps"></a>後續步驟

若要將功能加入至您的應用程式，請選取中的項目**資料來源**視窗並將它拖曳至表單，以建立繫結的控制項。 如需詳細資訊，請參閱[控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)