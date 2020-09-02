---
title: 如何：連接至服務中的資料 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654695"
---
# <a name="how-to-connect-to-data-in-a-service"></a>如何：連接至服務中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以執行 [[資料來源設定向導](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)]，然後在 [**選擇資料來源類型**] 頁面上選取 [**服務**]，將應用程式連接到從服務傳回的資料。

 完成嚮導之後，服務參考即會加入至您的專案，並且可立即在 [ [資料來源] 視窗](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)中使用。

> [!NOTE]
> [資料來源]**** 視窗中所顯示的項目，取決於服務所傳回的資訊。 部分服務所提供的資訊可能不足，無法供 [資料來源組態精靈]**** 建立可繫結的物件。 例如，如果服務傳回不具類型的資料集，則完成嚮導時，[ **資料來源] 視窗** 中不會出現任何專案。 這是因為不具類型的資料集不提供架構，所以 wizard 沒有足夠的資訊來建立資料來源。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>將您的應用程式連線至服務

1. 在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。

2. 在 [**選擇資料來源類型**] 頁面上選取 [**服務**]，然後按 **[下一步]**。

3. 輸入您想要使用之服務的位址，或按一下 [ **探索** ] 以找出目前解決方案中的服務，然後按一下 [ **移至**]。

4. 您可以選擇性地輸入新的 **命名空間** 來取代預設值。

    > [!NOTE]
    > 按一下 [ **Advanced** ] 以開啟 [ [設定服務參考] 對話方塊](../data-tools/configure-service-reference-dialog-box.md)。

5. 按一下 **[確定]** ，將服務參考加入至您的專案。

6. 按一下 [完成]  。

     資料來源隨即新增至 [資料來源]**** 視窗。

## <a name="next-steps"></a>後續步驟

#### <a name="to-add-functionality-to-your-application"></a>加入應用程式的功能

- 在 [ **資料來源** ] 視窗中選取專案，然後將它拖曳到表單上，以建立繫結控制項。 如需詳細資訊，請參閱 [將控制項系結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱
 在 Visual Studio 中[將 WPF 控制項系結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [Windows Communication Foundation 服務和 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
