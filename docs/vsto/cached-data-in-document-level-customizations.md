---
title: "快取文件層級自訂中的資料 |Microsoft 文件"
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
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f90aeb03dd62d76064124e9870a5a4dbcd250621
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="cached-data-in-document-level-customizations"></a>文件層級自訂中的快取資料
  文件層級自訂的主要目標是將資料從 Office 文件中的檢視。 資料是指儲存在文件，包括數字和文字中的資訊。 檢視是指使用者介面和 Microsoft Office Word 和 Microsoft Office Excel 物件模型。  
  
 Visual Studio 的資料加以區分從檢視文件層級自訂中藉由啟用資料會內嵌為*資料島*，也稱為*資料快取*。 您可以讀取或修改直接啟動 Word 或 Excel 的資料。 當您需要修改並沒有安裝 Microsoft Office 的伺服器上的文件中的資料時，這非常有用。 Word 和 Excel 都適用於用戶端環境。它們不被為了在伺服器上執行。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 如需文件層級自訂的詳細資訊，請參閱[Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)和[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
## <a name="understanding-the-cached-data-programming-model"></a>了解快取的資料程式設計模型  
 資料島可以包含任何符合特定需求的方案中的物件。 這些物件包括<xref:System.Data.DataSet>物件<xref:System.Data.DataTable>物件和任何其他物件可以序列化的<xref:System.Xml.Serialization.XmlSerializer>類別。 如需詳細資訊，請參閱 < 請參閱[快取資料](../vsto/caching-data.md)。  
  
 若要檢視提供快取的資料，您可以繫結 Windows Form 控制項和*主控制項*文件中的資料島的物件。 資料島與資料繫結控制項之間的資料繫結，可讓兩者同步處理。 您也可以加入驗證程式碼無關的控制項的資料。 如需詳細資訊，請參閱[資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 主控制項被擴充原生 Excel 和 Word 物件模型中的物件的版本。 不同於原生的物件，主控制項可以是直接繫結至受管理的資料物件。 如需詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) 與 [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
## <a name="accessing-cached-data-on-the-server"></a>存取伺服器上的快取的資料  
 若要存取文件中的快取的資料，您可以使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別。 這個類別是部分[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，並且能在沒有執行的 Excel 或 Word 的伺服器上。 當使用者開啟文件之後您修改快取的資料，任何控制項繫結至資料變更，都會自動同步處理，且使用者會看到更新的資料。 如需詳細資訊，請參閱 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 Excel 和 Word 不需要在伺服器上，以檢視用戶端上寫入資料。 Excel 和 Word 甚至不必安裝在伺服器上。 此提供改善的延展性和快速執行批次處理含有資料島的文件的能力。  
  
## <a name="data-caching-for-offline-use"></a>資料快取供離線使用  
 將資料儲存在資料島啟用離線案例。 當使用者第一次開啟文件或文件會向伺服器要求時，使用最新的資料填入資料島。 資料島會快取文件中，然後可離線瀏覽。 使用者 （和您的程式碼） 可以操作資料，即使沒有即時連接可用。 當使用者重新連線時，資料變更可傳播回伺服器資料來源。  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>快取的資料和自訂 XML 組件的比較  
 自訂 XML 組件是在 2007 Microsoft Office system 中導入，以儲存任意 XML 文件中的方法。 雖然自訂 XML 組件可用於許多做為資料快取相同的案例，有一些資料島與自訂 XML 組件之間的差異。 如需有關自訂 XML 組件的詳細資訊，請參閱[自訂 XML 組件概觀](../vsto/custom-xml-parts-overview.md)。  
  
 下表列出一些差異和相似性。  
  
||資料快取|自訂 XML 組件|  
|-|----------------|----------------------|  
|Office 應用程式可以使用這些？|下列應用程式的文件層級自訂：<br /><br /> Excel<br />字組|下列應用程式的文件層級和應用程式層級方案：<br /><br /> Excel<br />-PowerPoint<br />字組|  
|您可以儲存的資料類型？|您符合特定需求的自訂組件中的任何公用物件。 如需詳細資訊，請參閱 [Caching Data](../vsto/caching-data.md)。|任何 XML 資料。|  
|您可以存取的資料而不啟動 Microsoft Office 應用程式嗎？|是，透過使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別所提供[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。|是，使用中的類別來<xref:System.IO.Packaging>命名空間，或使用 Open XML 格式 SDK。|  
  
## <a name="see-also"></a>另請參閱  
 [在 Office 方案中的資料](../vsto/data-in-office-solutions.md)   
 [Office 方案在 Visual Studio 中的架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  