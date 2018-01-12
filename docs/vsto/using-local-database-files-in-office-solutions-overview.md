---
title: "使用 Office 方案概觀中的本機資料庫檔案 |Microsoft 文件"
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
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1576af3c3fc8a1c7f514a4941eb849df03774c5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="using-local-database-files-in-office-solutions-overview"></a>使用在 Office 方案概觀中的本機資料庫檔案
  您可以包含資料庫檔案，例如 SQL Server Express (.mdf) 檔案或 Microsoft Office Access (.mdb) 檔案，在 Office 方案中。 這可讓使用者維護的情況下維護集中式的資料庫不必要的例如在使用單一電腦的本機庫存方案中的本機資料庫。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="importing-the-database-file-into-a-project"></a>資料庫檔案匯入專案  
 若要將資料庫檔案匯入您的專案，使用**資料來源組態精靈**來建立資料庫檔案為基礎的資料來源。 精靈會將資料庫檔案和具類型資料集加入至您的專案。  
  
## <a name="deploying-the-database-file"></a>部署資料庫檔案  
 **資料來源組態精靈**使用相對路徑建立連接至本機資料庫檔案。 這可讓您的方案從某部電腦複製到另一個在您所維護的檔案的相對位置。  
  
 如果您將方案部署至伺服器，然後散發給每位使用者的文件時，必須手動散發資料庫檔案，並將它安裝在相同文件的相對位置。 這表示使用者無法移動到新位置的文件他或她在電腦上，除非他或她也會移動資料庫檔案。  
  
## <a name="local-database-files-and-caching-the-dataset"></a>本機資料庫檔案和快取資料集  
 在 Microsoft Office Excel 和 Microsoft Office Word 文件層級方案中，您可以在快取文件中的資料集來標記與屬性的資料集執行個體<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>。 當您將資料庫檔案加入您的專案使用**資料來源組態精靈**，自動具類型資料集加入至您的專案。 它是很少會需要套用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>此資料集，因為資料已在本機使用者的電腦上。 如需詳細資訊，請參閱 [Caching Data](../vsto/caching-data.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何： 從資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何： 從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [快取資料](../vsto/caching-data.md)  
  
  