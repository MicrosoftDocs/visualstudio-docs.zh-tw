---
title: 使用本機資料庫檔案，在 Office 方案概觀
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eec0a2adcb462bd2bb169cb997ce2fe352b0c72a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872699"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>使用本機資料庫檔案，在 Office 方案概觀
  您可以包含資料庫檔案，例如 SQL Server Express (*.mdf*) 檔案或 Microsoft Office Access (*.mdb*) 檔案，請在您的 Office 解決方案。 這可讓使用者在其中維護集中式的資料庫不是必要項，例如在單一電腦使用本機的清查解決方案的情況下本機資料庫的維護。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="import-the-database-file-into-a-project"></a>資料庫檔案匯入專案  
 若要匯入專案的資料庫檔案，使用**資料來源組態精靈**來建立資料庫檔案為基礎的資料來源。 精靈會將資料庫檔案和具類型資料集加入至您的專案。  
  
## <a name="deploy-the-database-file"></a>將資料庫檔案部署  
 **資料來源組態精靈**建立本機資料庫檔案的連線會使用相對路徑。 這可讓您的解決方案從某部電腦複製到另一個如果要維護的檔案的相對位置。  
  
 如果您將方案部署至伺服器，然後散發給每位使用者的文件時，您就必須手動散發資料庫的檔案，並將它安裝在相同的位置，相對於文件。 這表示使用者無法移到新位置的文件他或她在電腦上，除非他或她也會移動資料庫檔案。  
  
## <a name="local-database-files-and-caching-the-dataset"></a>本機資料庫檔案和快取資料集  
 在 Microsoft Office Excel 和 Microsoft Office Word 的文件層級解決方案，您可以由快取文件中的資料集將資料集執行個體，以屬性標示<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>。 當您將資料庫檔案加入您的專案使用**資料來源組態精靈**，具類型資料集自動新增至您的專案。 很少需要套用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>到此資料集，因為資料已是本機使用者的電腦上。 如需詳細資訊，請參閱 <<c0> [ 快取資料](../vsto/caching-data.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何：資料庫中的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [快取資料](../vsto/caching-data.md)  
