---
title: 文件層級自訂中的快取的資料
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0710f196e6572cf6bc9851d8a765758fcb43326d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671488"
---
# <a name="cached-data-in-document-level-customizations"></a>文件層級自訂中的快取的資料
  文件層級自訂的主要目標是將資料從 Office 文件中的檢視。 資料是指儲存在文件，包括數字和文字的資訊。 檢視是指使用者介面和 Microsoft Office Word 和 Microsoft Office Excel 物件模型。  
  
 Visual Studio 將從 文件層級自訂中檢視資料，藉由啟用要內嵌為資料*資料島*，也稱為*資料快取*。 您可以讀取或修改的資料直接而不啟動 Word 或 Excel。 當您需要修改並沒有安裝 Microsoft Office 的伺服器上的文件中的資料時，這非常有用。 Word 和 Excel 被適用於用戶端環境;它們不適用於在伺服器上執行。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 如需文件層級自訂的詳細資訊，請參閱[Office 方案開發概觀&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)並[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
## <a name="understand-the-cached-data-programming-model"></a>了解快取的資料程式設計模型  
 資料島可以包含在您符合特定需求的解決方案中任何物件。 這些物件包含<xref:System.Data.DataSet>物件<xref:System.Data.DataTable>物件和任何其他物件可以序列化的<xref:System.Xml.Serialization.XmlSerializer>類別。 如需詳細資訊，請參閱 <<c0> [ 快取資料](../vsto/caching-data.md)。  
  
 若要提供快取的資料檢視，您可以繫結 Windows Form 控制項和*主控制項*文件，資料島中的物件。 資料島和資料繫結控制項之間的資料繫結會保留這兩個同步處理。 您也可以將驗證程式碼無關的控制項的資料。 如需詳細資訊，請參閱 <<c0> [ 將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 主控制項被擴充原生 Excel 和 Word 物件模型中的物件的版本。 不同於原生的物件，主控制項可以繫結直接受管理的資料物件。 如需詳細資訊，請參閱 <<c0> [ 主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)並[Windows Forms 控制項上 Office 文件概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
## <a name="access-cached-data-on-the-server"></a>存取快取伺服器上的資料  
 若要存取文件中的快取的資料，您可以使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別。 這個類別屬於[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，而且它可用在沒有執行的 Excel 或 Word 的伺服器上。 當使用者開啟文件，在後修改快取的資料，任何資料繫結的控制項都會自動同步處理的變更，而使用者會看到更新的資料。 如需詳細資訊，請參閱 <<c0> [ 存取在伺服器上的文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 Excel 和 Word，不需要在伺服器上，以檢視用戶端上寫入的資料。 Excel 和 Word 甚至不必安裝在伺服器上。 這提供改良的延展性和執行快速的批次處理，包含資料島的文件的能力。  
  
## <a name="data-caching-for-offline-use"></a>資料快取供離線使用  
 將資料儲存在資料島可離線案例。 當使用者第一次開啟文件，或從伺服器要求文件時，資料島會填入最新的資料。 資料島會快取文件中，就可以離線。 使用者 （和您的程式碼） 可以操作資料，即使有可用的任何即時連線。 當使用者重新連接時，資料的變更可以傳播回到伺服器資料來源中。  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>快取的資料和自訂 XML 組件的比較  
 自訂 XML 組件引進在 2007 Microsoft Office system 文件中儲存任意的 XML 片段的方式。 雖然自訂 XML 組件的許多資料快取為相同的案例中很有用，但是有一些資料島和自訂 XML 組件之間的差異。 如需有關自訂 XML 組件的詳細資訊，請參閱 <<c0> [ 自訂 XML 組件概觀](../vsto/custom-xml-parts-overview.md)。  
  
 下表列出一些差異和相似性。  
  
||資料快取|自訂 XML 組件|  
|-|----------------|----------------------|  
|哪些 Office 應用程式可以使用這些？|下列應用程式的文件層級自訂：<br /><br /> Excel<br />字組|下列應用程式的文件層級和應用程式層級解決方案：<br /><br /> Excel<br />-PowerPoint<br />字組|  
|您可以儲存的資料類型？|您符合特定需求的自訂組件中的任何公用物件。 如需詳細資訊，請參閱 <<c0> [ 快取資料](../vsto/caching-data.md)。|任何的 XML 資料。|  
|您可以存取的資料而不啟動 Microsoft Office 應用程式嗎？|是的是藉由使用<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>所提供的類別[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。|是的是藉由使用中的類別<xref:System.IO.Packaging>命名空間，或使用 Open XML 格式 SDK。|  
  
## <a name="see-also"></a>另請參閱  
 [在 Office 方案中的資料](../vsto/data-in-office-solutions.md)   
 [在 Visual Studio 中的 Office 方案的架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  