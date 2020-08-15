---
title: 檔層級自訂中的快取資料
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9985dd25ba62cc9c0735a8a8f4008a4c0abe0558
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238344"
---
# <a name="cached-data-in-document-level-customizations"></a>檔層級自訂中的快取資料
  檔層級自訂的主要目標是要在 Office 檔中分開查看資料。 資料指的是儲存在檔中的資訊，包括數位和文字。 View 指的是使用者介面，以及 Microsoft Office Word 和 Microsoft Office Excel 的物件模型。

 Visual Studio 將資料內嵌為 *資料島*（也稱為 *資料*快取），以在檔層級自訂中將資料與視圖分開。 您可以直接讀取或修改資料，而不需要啟動 Word 或 Excel。 當您需要在未安裝 Microsoft Office 的伺服器上修改檔中的資料時，這會很有用。 Word 和 Excel 的目的是要在用戶端環境中使用;它們不是設計成要在伺服器上執行。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 如需檔層級自訂的詳細資訊，請參閱 [Office 方案開發總覽 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) 和 [檔層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。

## <a name="understand-the-cached-data-programming-model"></a>瞭解快取的資料程式設計模型
 資料島可以包含符合特定需求之解決方案中的任何物件。 這些物件包括 <xref:System.Data.DataSet> 物件、 <xref:System.Data.DataTable> 物件，以及可由類別序列化的任何其他物件 <xref:System.Xml.Serialization.XmlSerializer> 。 如需詳細資訊，請參閱快取 [資料](../vsto/caching-data.md)。

 若要提供快取資料的視圖，您可以將檔上的 Windows Forms 控制項和 *主控制項* 系結至資料島中的物件。 資料島和資料繫結控制項之間的資料系結會讓兩個同步處理。 您也可以將驗證程式代碼加入與控制項無關的資料。 如需詳細資訊，請參閱 [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

 主控制項是 Excel 和 Word 物件模型中的原生物件擴充版本。 不同于原生物件，主控制項可以直接系結至 managed 資料物件。 如需詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md) 和 [Office 檔上的 Windows Forms 控制項總覽](../vsto/windows-forms-controls-on-office-documents-overview.md)。

## <a name="access-cached-data-on-the-server"></a>存取伺服器上的快取資料
 若要存取檔中的快取資料，您可以使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別。 這個類別是的一部分 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ，而且可以在伺服器上使用，而不需要執行 Excel 或 Word。 當使用者在您修改快取的資料之後開啟檔時，系結至資料的任何控制項都會自動同步處理至變更，而使用者會看到更新的資料。 如需詳細資訊，請參閱在 [伺服器上存取檔中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。

 Excel 和 Word 不需要寫入伺服器上的資料，只能在用戶端上進行查看。 Excel 和 Word 甚至不需要安裝在伺服器上。 這可提供改良的擴充性，並能夠對包含資料島的檔執行快速批次處理。

## <a name="data-caching-for-offline-use"></a>供離線使用的資料快取
 將資料儲存在資料島中可啟用離線案例。 當使用者第一次開啟檔或向伺服器要求檔時，資料島會填入最新的資料。 資料島會在檔中快取，然後可以在離線時使用。 使用者 (和您的程式碼) 可以操控資料，即使沒有即時連線可供使用也一樣。 當使用者重新連線時，對資料所做的變更會傳播回到伺服器資料來源。

## <a name="cached-data-and-custom-xml-parts-compared"></a>相較于快取資料和自訂 XML 元件
 自訂 XML 元件是在 2007 Microsoft Office 系統中引進，做為在檔中儲存任意 XML 片段的方式。 雖然自訂 XML 元件在許多與資料快取相同的案例中很有用，但資料島和自訂 XML 元件之間有一些差異。 如需自訂 XML 元件的詳細資訊，請參閱 [自訂 xml 元件總覽](../vsto/custom-xml-parts-overview.md)。

 下表列出一些差異和相似性。

|問題/特性|資料快取|自訂 XML 元件|
|-|----------------|----------------------|
|哪些 Office 應用程式可以使用這些專案？|下列應用程式的檔層級自訂：<br /><br /> -Excel<br />-Word|適用于下列應用程式的檔層級和應用層級解決方案：<br /><br /> -Excel<br />-PowerPoint<br />-Word|
|您可以儲存哪些類型的資料？|自訂群組件中符合特定需求的任何公用物件。 如需詳細資訊，請參閱快取 [資料](../vsto/caching-data.md)。|任何 XML 資料。|
|您是否可以在不啟動 Microsoft Office 應用程式的情況下存取資料？|是，使用所 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 提供的類別 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 。|可以，方法是使用命名空間中的類別 <xref:System.IO.Packaging> ，或使用 OPEN XML 格式 SDK。|

## <a name="see-also"></a>另請參閱
- [Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [Visual Studio 中的 Office 方案架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)
