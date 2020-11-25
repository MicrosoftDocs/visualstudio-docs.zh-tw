---
title: 沙箱化解決方案考慮 |Microsoft Docs
description: 探索沙箱化方案，這是 Microsoft SharePoint 中的一項功能，可讓網站集合使用者上傳自己的自訂程式碼解決方案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 17b310a3f992f80b04ad14bb6e038e05b009a4af
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970465"
---
# <a name="sandboxed-solution-considerations"></a>沙箱化解決方案考慮
  *沙箱化方案* 是 Microsoft SharePoint 2010 中的一項功能，可讓網站集合使用者上傳自己的自訂程式碼解決方案。 常見的沙箱化解決方案是使用者上傳自己的 Web 組件。

 沙箱化 SharePoint 應用程式是在安全且受監視的進程中執行，該進程可以存取 Web 伺服陣列的有限部分。 Microsoft SharePoint 2010 使用功能、方案庫、解決方案監視和驗證架構的組合，以啟用沙箱化解決方案。

## <a name="specify-project-trust-level"></a>指定專案信任層級
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 透過稱為 *沙箱化方案* 的布林值專案屬性支援沙箱化方案。 您可以在專案中隨時設定這個屬性，也可以在 [ **SharePoint 自訂嚮導]** 中建立專案時指定此屬性。

> [!NOTE]
> 在專案建立之後變更其 *沙箱化方案* 屬性，可能會導致驗證錯誤。

 如果 [ *沙箱化方案* ] 屬性設定為 [ **false** ]，或選擇 [ **部署為數組方案** ] 選項，則方案會視為伺服器陣列範圍的方案。 但是，如果 *沙箱化方案* 屬性設為 **true** ，或您在嚮導中選擇 [ **部署為沙箱化方案** ] 選項，則會以不同于伺服器陣列方案的方式處理方案。

## <a name="sharepoint-site-hierarchy"></a>SharePoint 網站階層
 為了瞭解沙箱化解決方案的運作方式，它有助於知道 SharePoint 網站的範圍是階層式的。 最上層元素稱為 Web 伺服陣列，而其他專案則是附屬專案：

 Web 伺服陣列

 Web 應用程式 A

 網站集合 A1

 網站 A1a

 Web 應用程式 B

 Site Collection B1

 網站 B1a

 網站 B1b

 網站集合 B2

 網站 B2a

 如您所見，Web 伺服陣列可包含一或多個 Web 應用程式，而這些應用程式可能會包含一或多個網站集合，而這些應用程式可能會有子網站等等。 對單一網站集合所做的變更只會影響該網站集合，而不會影響其他網站集合。 不過，在 Web 伺服陣列層級所做的變更會影響伺服器陣列上的所有網站集合。

 Windows SharePoint Services (WSS) 3.0 可讓您只將方案部署至伺服器陣列層級，但可 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 讓您部署至伺服器陣列層級 (伺服器陣列方案) 或網站集合層級 (沙箱化方案) 。

## <a name="why-sandboxed-solutions"></a>為何要進行沙箱化解決方案？
 在 WSS 3.0 中，方案只能部署至伺服器陣列層級。 這表示可能會部署可能有害或不穩定的解決方案，其會影響整個 Web 伺服陣列，以及在其下執行的所有其他網站集合和應用程式。 不過，您可以使用沙箱化方案，將您的方案部署至伺服器陣列的子領域，也就是特定的網站集合。 為了提供額外的保護，解決方案的元件不會載入至主要 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 進程 (*w3wp.exe*) 。 相反地，它會載入至不同的進程， (*SPUCWorkerProcess.exe*) 。 此程式會受到監視，並會執行配額和節流，以保護伺服器陣列免于執行有害活動的沙箱化解決方案，例如執行耗用 CPU 迴圈的緊密迴圈。

## <a name="site-collection-solution-gallery"></a>網站集合解決方案資源庫
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 有一項稱為「方案庫網站集合」的功能。 您可以從 SharePoint 2010 管理中心頁面存取這項功能，或開啟 [**網站動作**] 功能表，選擇 **[網站設定**]，然後選擇 SharePoint 網站中 [資源 **庫**] 下的 [**方案**] 連結。 解決方案資源庫是解決方案的儲存機制，可讓網站集合管理員管理其網站集合中的解決方案。

 方案庫是儲存在 SharePoint 網站根 Web 的文件庫。 解決方案庫會取代網站範本，並支援解決方案套件。 上傳 SharePoint 方案套件 (*.wsp*) 檔案時，就會將它視為沙箱化方案進行處理。

## <a name="sandboxed-solution-limitations"></a>沙箱化方案限制
 當您部署沙箱化方案時，可供它使用的 SharePoint 功能陣列會受到限制，以協助降低可能發生的任何安全性弱點。 其中一些限制包括下列各項：

- 沙箱化解決方案具有可供使用的可部署解決方案專案的有限子集。 可能有很容易使用的 SharePoint 專案範本，例如網站定義和工作流程。

- SharePoint 會在進程中執行沙箱化方案程式碼 (*SPUCWorkerProcess.exe*) 與主要 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 應用程式集區不同， (*w3wp.exe*) 處理常式。

- 無法將對應資料夾新增至專案。

- 元件中的類型 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 不能用於沙箱化方案中。 此外，只有元件中的類型 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 可以用於沙箱化方案。

  請務必注意，將 SharePoint 方案指定為沙箱化方案，對 SharePoint 伺服器不會有任何影響;它只會決定 SharePoint 專案的部署方式，以及它所系結的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 元件。 它不會影響產生的 *.wsp* 檔案，而且 *.wsp* 檔案沒有直接與 *沙箱化方案* 屬性相互關聯的資料。

## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>沙箱化方案中的功能和元素
 沙箱化解決方案支援下列功能和元素：

- 內容類型/欄位

- 自訂動作

- 宣告式工作流程

- 事件接收器

- 功能標注

- 列出定義

- 列出實例

- 模組/檔案

- 導覽

- *Onet.xml*

- SPItemEventReceiver

- SPListEventReceiver

- SPWebEventReceiver

- 支援所有衍生自的 Web 組件 `System.Web.UI.WebControls.WebParts.WebPart`

- Web 組件

- WebTemplate 功能元素 (，而不是 *Webtemp.xml*) 

- Visual Web 組件

  沙箱化解決方案不支援下列功能和元素：

- 應用程式頁面

- 自訂動作群組

- 伺服器陣列範圍的功能

- `HideCustomAction` 項目

- Web 應用程式範圍的功能

- 具有程式碼的工作流程

## <a name="see-also"></a>另請參閱
- [沙箱化與伺服器陣列方案之間的差異](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
