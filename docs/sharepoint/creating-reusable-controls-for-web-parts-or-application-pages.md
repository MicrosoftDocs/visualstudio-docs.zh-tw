---
title: 針對 Web 組件或應用程式頁面建立可重複使用的控制項 |Microsoft Docs
titleSuffix: ''
description: 在 Visual Studio 中建立可重複使用的自訂控制項 (使用者控制項) ，可供在 SharePoint 中執行的應用程式頁面和 web 元件使用。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 01d8602971e2a89aef8cf8451d1273fa28c70f05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949125"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>為 web 元件或應用程式頁面建立可重複使用的控制項
  在 Visual Studio 中，您可以為 SharePoint 中執行的應用程式頁面和 Web 組件，建立可供其利用之自訂、可重複使用的控制項。 這些控制項稱為使用者控制項。 使用者控制項是一種相當於 ASP.NET 網頁的複合控制項，您可以將現有的 Web 服務器控制項和標記加入至使用者控制項，並定義控制項的屬性和方法。 然後，您可以將它們內嵌在 ASP.NET 網頁中，作為一個單位。

## <a name="create-a-user-control"></a>建立使用者控制項
 若要建立使用者控制項，請將 **使用者控制項** 加入 **空白的 SharePoint 專案**。 如需詳細資訊，請參閱 [如何：建立 SharePoint 應用程式的使用者控制項頁面或網頁元件](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)。

 當您加入 **使用者控制項** 專案時，Visual Studio 會在專案中建立資料夾，然後將數個檔案加入至資料夾。 下表說明每個檔案。

|檔案|描述|
|----------|-----------------|
|使用者控制檔案|定義使用者控制項。 在這個檔案中加入控制項和標記，以設計使用者控制項。|
|程式碼檔案|包含使用者控制項背後的程式碼。 加入程式碼來處理這個檔案的事件。|
|設計工具程式碼檔案|包含由設計工具產生的程式碼，不應該直接編輯。|

## <a name="design-the-user-control"></a>設計使用者控制項
 使用 Visual Studio 中的 Visual Web Developer designer 來設計使用者控制項。 當您在專案中開啟使用者控制項檔案並選擇 [ **設計** ] 索引標籤時，就會出現這個設計工具。

## <a name="consume-the-user-control"></a>使用使用者控制項
 除非您將使用者控制項包含在應用程式頁面或 Web 元件中，否則使用者控制項不會出現在 SharePoint 中。

 若要將使用者控制項包含在應用程式頁面中，請開啟您要加入 ASP.NET 使用者控制項的網頁。 切換至設計檢視，然後在方案總管中選取您的自訂使用者控制項檔案，然後將它拖曳到頁面上。 ASP.NET 使用者控制項會加入至頁面，而設計工具會建立 @ Register 指示詞，頁面必須有此指示詞才能辨識使用者控制項。 您現在可以使用控制項的公用屬性和方法。

 若要在 Web 元件中包含使用者控制項，請將使用者控制項加入 web 元件程式碼檔案中的 Web 元件 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 集合。 下列範例會將使用者控制項加入至 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 網頁元件的集合。

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>調試使用者控制項
 若要對使用者控制項進行偵錯工具，請確定使用者控制項包含在 SharePoint 專案的應用程式頁面或 Web 元件中。 然後您就可以在使用者控制項中進行程式碼的偵錯工具，就像在任何 Visual Studio 專案中的程式碼一樣。

 當您啟動 Visual Studio 偵錯工具時，Visual Studio 會開啟 SharePoint 網站。

 在 SharePoint 中，開啟包含使用者控制項的應用程式頁面。 如果使用者控制項包含在 Web 元件中，請將網頁元件新增至 SharePoint 中的 Web 元件頁面。

 如需有關偵錯工具 SharePoint 專案的詳細資訊，請參閱 [疑難排解 sharepoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[如何：為 SharePoint 應用程式頁面或 web 元件建立使用者控制項](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|說明如何建立可供應用程式頁面使用的自訂、可重複使用的控制項，以及在 SharePoint 中執行的 Web 組件。|
