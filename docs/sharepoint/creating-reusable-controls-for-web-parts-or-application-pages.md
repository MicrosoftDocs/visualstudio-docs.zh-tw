---
title: "為 Web 組件或應用程式頁面建立可重複使用的控制項 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 02847ae640f969d3c330b5eb573f36c74ef07a2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-reusable-controls-for-web-parts-or-application-pages"></a>為 Web 組件或應用程式頁面建立可重複使用的控制項
  在 Visual Studio 中，您可以為 SharePoint 中執行的應用程式頁面和 Web 組件，建立可供其利用之自訂、可重複使用的控制項。 這些控制項稱為使用者控制項。 使用者控制項是一種運作方式十分類似 ASP.NET Web 網頁的複合控制項，您可以將現有的 Web 伺服器控制項和標記加入至使用者控制項，並定義控制項的屬性和方法。 您接著可以將其內嵌在 ASP.NET Web pages，它們做為一個單位的位置。  
  
## <a name="creating-a-user-control"></a>建立使用者控制項  
 若要建立使用者控制項，加入**使用者控制項**至**空白的 SharePoint 專案**。 如需詳細資訊，請參閱[How to： 建立 SharePoint 應用程式頁面或 Web 組件的使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)。  
  
 當您將加入**使用者控制項**Visual Studio 項目，在您的專案，建立資料夾並將數個檔案新增至資料夾。 下表描述每個檔案。  
  
|檔案|描述|  
|----------|-----------------|  
|使用者控制項檔案|定義使用者控制項。 將控制項和標記加入至這個檔案來設計使用者控制項。|  
|程式碼檔案|包含使用者控制項背後的程式碼。 加入程式碼來處理此檔案的事件。|  
|設計工具程式碼檔案|包含設計工具所產生的程式碼，且不應直接編輯。|  
  
## <a name="designing-the-user-control"></a>設計使用者控制項  
 使用 Visual Studio 中的 Visual Web Developer 設計工具來設計使用者控制項。 此設計工具隨即出現在您開啟專案中的使用者控制項檔案並選擇**設計** 索引標籤。  

## <a name="consuming-the-user-control"></a>使用使用者控制項  
 使用者控制項不會出現在 SharePoint 中直到您將它們包含在應用程式頁面或 Web 組件中。  
  
 若要將使用者控制項包含在應用程式頁面上，開啟您要將 ASP.NET 使用者控制項的網頁。 切換至 設計 檢視中，然後在方案總管 中，選取您的自訂使用者控制項檔案並將它拖曳到頁面。 ASP.NET 使用者控制項加入至頁面，並在設計工具建立 @ Register 指示詞，所需的頁面以辨識使用者控制項。 您現在可以使用控制項的公用屬性和方法。  
  
 若要包含 Web 組件中的使用者控制項，將使用者控制項加入至 Web 組件<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web 組件程式碼檔案中的集合。 下列範例會將使用者控制項加入<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web 組件的集合。  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debugging-a-user-control"></a>偵錯的使用者控制項  
 偵錯的使用者控制項，請確定使用者控制項包含在應用程式頁面或 Web 組件在 SharePoint 專案中。 就像您會在任何 Visual Studio 專案中的程式碼進行偵錯，您接著可以偵錯使用者控制項中的程式碼。  
  
 當您啟動 Visual Studio 偵錯工具時，Visual Studio 會開啟 SharePoint 網站。  
  
 在 SharePoint 中，開啟應用程式頁面，其中包含使用者控制項。 如果 Web 組件中包含使用者控制項，加入 Web 組件中的頁面 SharePoint Web 組件。  
  
 如需有關偵錯 SharePoint 專案的詳細資訊，請參閱[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[如何：為 SharePoint 應用程式頁面或 Web 組件建立使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|示範如何建立可由應用程式頁面和 Web 組件，在 SharePoint 中執行的自訂、 可重複使用控制項。|  
  
  