---
title: HOW TO：連接到服務中的資料 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 62cbbd63f38e3317b03b203b3ca1cadc2a17e0c3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386104"
---
# <a name="how-to-connect-to-data-in-a-service"></a>HOW TO：連線至服務中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

連接您的應用程式，執行從服務傳回的資料[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)，然後選取**服務**上**選擇資料來源類型**頁面。  
  
 完成精靈的詳細資訊，服務參考加入至專案並立即提供[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)。  
  
> [!NOTE]
> [資料來源] 視窗中所顯示的項目，取決於服務所傳回的資訊。 部分服務所提供的資訊可能不足，無法供 [資料來源組態精靈] 建立可繫結的物件。 例如，如果服務傳回不具類型的資料集，然後顯示任何項目中**資料來源視窗**時正在完成精靈。 這是因為不具類型資料集不會提供結構描述，所以精靈沒有足夠的資訊來建立資料來源。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>若要連接至服務的應用程式  
  
1. 在 [ **資料** ] 功能表上，請按一下 [ **加入新資料來源**]。  
  
2. 選取 [**服務**上**選擇資料來源類型**頁面，然後再按一下**下一步]**。  
  
3. 輸入您想要使用，或按一下 服務的位址**Discover**以在目前的方案中，尋找服務，然後按一下**移**。  
  
4. （選擇性） 的新**命名空間**可以類型來取代預設的值。  
  
    > [!NOTE]
    > 按一下 [**進階**來開啟[設定服務參考對話方塊]](../data-tools/configure-service-reference-dialog-box.md)。  
  
5. 按一下 **確定**加入服務參考加入專案。  
  
6. 按一下 [ **完成**]。  
  
     資料來源隨即新增至 [資料來源] 視窗。  
  
## <a name="next-steps"></a>後續步驟  
  
#### <a name="to-add-functionality-to-your-application"></a>加入應用程式的功能  
  
- 選取中的項目**Zdroje dat**視窗並將它拖曳至表單，以建立繫結的控制項。 如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
