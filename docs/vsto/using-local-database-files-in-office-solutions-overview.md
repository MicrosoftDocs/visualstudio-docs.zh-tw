---
title: 在 Office 方案中使用本機資料庫檔案總覽
description: 瞭解如何在 Office 方案中包含資料庫檔案，例如 SQL Server Express ( .mdf) 檔或 Microsoft Office 存取 ( .mdb) 檔案。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1a3166a88080eaee1042187c171c4938d236058a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526553"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>在 Office 方案中使用本機資料庫檔案總覽
  您可以在 Office 方案中包含資料庫檔案，例如 SQL Server Express (*.mdf*) 檔或 Microsoft Office 存取 (*.mdb*) 檔案。 這可讓使用者在不需要維護集中式資料庫的情況下維護本機資料庫，例如，只在單一電腦上使用的本機清查解決方案。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>將資料庫檔案匯入專案中
 若要將資料庫檔案匯入到您的專案中，請使用 [ **資料來源設定] Wizard** 根據資料庫檔案建立資料來源。 Wizard 會將資料庫檔案和具類型的資料集加入至您的專案。

## <a name="deploy-the-database-file"></a>部署資料庫檔案
 **資料來源設定向導** 會使用相對路徑來建立本機資料庫檔案的連接。 如果您維護檔案的相對位置，這可讓您將方案從一部電腦複製到另一部電腦。

 如果您將方案部署至伺服器，然後將檔散發給每位使用者，您也必須手動散發資料庫檔案，並將它安裝在相對於檔的相同位置。 這表示使用者不能將檔移至電腦上的新位置，除非他或她也移動資料庫檔案。

## <a name="local-database-files-and-caching-the-dataset"></a>本機資料庫檔案和快取資料集
 在 Microsoft Office Excel 和 Microsoft Office Word 的檔層級方案中，您可以使用屬性標記資料集實例，以快取檔中的資料集 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 。 當您使用 [ **資料來源設定向導]** 將資料庫檔案加入至專案時，會自動將具類型的資料集加入至您的專案。 很少需要將此資料 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 集套用到這個資料集，因為資料已經是使用者電腦上的本機資料。 如需詳細資訊，請參閱快取 [資料](../vsto/caching-data.md)。

## <a name="see-also"></a>另請參閱
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [如何：使用資料庫的資料填入檔](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [快取資料](../vsto/caching-data.md)
