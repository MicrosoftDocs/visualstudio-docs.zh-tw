---
title: "多層式架構資料應用程式概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 3949d49f763c2513e86c2cd3f1b20c20fb858ecc
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="n-tier-data-applications-overview"></a>多層式架構資料應用程式概觀
*多層式架構*資料應用程式是分成多個資料應用程式*層*。 多層式架構應用程式也稱為 「 分散式應用程式 」 和 「 多層式應用程式 」，在個別分成離散層級用戶端與伺服器之間分散處理。 當您開發存取資料的應用程式時，您應該有清楚的區隔構成應用程式的各層之間。  
  
一般的多層式架構應用程式包含展示層、 中介層和資料層。 分隔各層中的多層式架構應用程式的最簡單方式是建立不同的專案，每個您想要包含在應用程式中的階層。 例如，展示層可能是 Windows Forms 應用程式，而資料存取邏輯可能位於中介層的類別庫。 此外，展示層可能會與資料存取邏輯中介層透過例如服務的服務進行通訊。 將應用程式元件分隔成不同的層級會提升應用程式的可維護性和延展性 (Scalability)。 它會更容易採用新技術，可套用至單一層，而不需要重新設計整個方案。 此外，多層式架構應用程式通常會儲存機密資訊在中介層，以維護與展示層的隔離。  
  
Visual Studio 包含可協助開發人員建立多層式架構應用程式的一些功能：  
  
-   資料集提供**資料集專案**屬性，可讓您分隔資料集 （資料實體層） 和 Tableadapter （資料存取層） 為離散專案。  
  
-   [LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)提供設定至不同的命名空間中產生的 DataContext 和資料類別。 這可讓資料存取與資料實體層的邏輯分隔。  
  
-   [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)提供<xref:System.Data.Linq.Table%601.Attach%2A>方法可讓您將應用程式中的不同層級的 DataContext 結合在一起。 如需詳細資訊，請參閱[N-tier 和遠端的應用程式以及 LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)。  
  
## <a name="presentation-tier"></a>展示層  
*展示層*使用者互動的應用程式層。 它通常會包含其他應用程式邏輯也。 典型的展示層元件包括：  
  
-   資料繫結元件，例如<xref:System.Windows.Forms.BindingSource>和<xref:System.Windows.Forms.BindingNavigator>。  
  
-   物件表示的資料，例如[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)展示層中使用的實體類別。  
  
使用 服務參考展示層通常存取的中介層 (例如， [Windows Communication Foundation 服務和 Visual Studio 中的 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)應用程式)。 展示層不會直接存取資料層。 展示層會與透過中介層的資料存取元件的資料層進行通訊。  
  
## <a name="middle-tier"></a>中介層  
*中介層*的圖層，展示層和資料層用來與對方進行通訊。 典型的中介層元件包括下列各項：  
  
-   商務邏輯，例如商務規則和資料驗證。  
  
-   資料存取元件與邏輯，如下所示：  
  
    -   [Tableadapter](create-and-configure-tableadapters.md)和[Dataadapter 和 Datareader](/dotnet/framework/data/adonet/dataadapters-and-datareaders)。  
  
    -   物件表示的資料，例如[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)實體類別。  
  
    -   一般應用程式服務，例如驗證、 授權及個人化。  
  
下圖顯示功能與技術，可提供 Visual Studio 中，而且它們可能適用於什麼情況的多層式架構應用程式的中介層。  
  
![中間層元件](../data-tools/media/ntiermid.png "NtierMid")  
中介層  
  
中介層通常會連接到資料層使用資料連接。 此資料連接通常會儲存在資料存取元件中。  
  
## <a name="data-tier"></a>資料層  
*資料層*基本上是儲存應用程式資料的伺服器 (例如，將執行的伺服器[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)])。  
  
下圖顯示功能與技術，可提供在 Visual Studio 中，而且它們可能適用於什麼情況的多層式架構應用程式的資料層。  
  
![資料層元件](../data-tools/media/ntierdatatier.png "ntierdatatier")  
資料層  
  
資料層無法直接從展示層中的用戶端存取。 相反地，資料存取元件中介層用於簡報和資料層之間的通訊。  
  
## <a name="help-for-n-tier-development"></a>多層式架構開發的說明  
下列主題提供有關使用多層式架構應用程式資訊：  
  
[將資料集和 TableAdapter 分成不同的專案](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
  
[逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  

[多層式架構和遠端的應用程式使用 LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)  
  
## <a name="see-also"></a>請參閱
[逐步解說： 建立 N-tier 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
[階層式更新](../data-tools/hierarchical-update.md)   
[Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)   
[存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)