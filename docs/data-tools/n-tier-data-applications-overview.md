---
title: 多層式架構資料應用程式概觀
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e4c10e3a337b44a4b7c9a1cb59165736bb3e7efb
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871533"
---
# <a name="n-tier-data-applications-overview"></a>多層式架構 (N-Tier) 資料應用程式概觀
多*層式*資料應用程式是分割成多*層*的資料應用程式。 多層式應用程式也稱為「分散式應用程式」和「多層式應用程式」, 可將處理分隔成在用戶端與伺服器之間散發的離散層。 當您開發可存取資料的應用程式時, 您應該在組成應用程式的各層之間有清楚的分隔。

一般的 N-Tier 應用程式包含展示層、中介層和資料層。 將多層式應用程式中的各層分開的最簡單方式, 就是為您想要包含在應用程式中的每一層建立離散專案。 例如, 展示層可能是 Windows Forms 應用程式, 而資料存取邏輯可能是位於中介層的類別庫。 此外, 展示層可能會透過 web 服務之類的服務, 與仲介層中的資料存取邏輯通訊。 將應用程式元件分隔成不同的層級會提升應用程式的可維護性和延展性 (Scalability)。 它的作法是讓您更輕鬆地採用可套用至單一層的新技術, 而不需要重新設計整個解決方案。 此外, 多層式應用程式通常會在仲介層中儲存機密資訊, 這會維護與展示層的隔離。

Visual Studio 包含數項功能, 可協助開發人員建立多層式應用程式:

- 資料集提供**資料集專案**屬性, 可讓您將資料集 (資料實體層) 和 tableadapter (資料存取層) 分隔成離散專案。

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)會提供將 DataCoNtext 和資料類別產生為不同命名空間的設定。 這會啟用資料存取和資料實體層的邏輯分隔。

- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)提供的<xref:System.Data.Linq.Table%601.Attach%2A>方法可讓您從應用程式中的不同層級整合 DataCoNtext。 如需詳細資訊, 請參閱[使用 LINQ to SQL 的多層式和遠端應用程式](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)。

## <a name="presentation-tier"></a>展示層
*展示層*是使用者與應用程式互動的層級。 它通常也會包含額外的應用程式邏輯。 一般展示層元件包括下列各項:

- 資料系結元件, 例如<xref:System.Windows.Forms.BindingSource>和。 <xref:System.Windows.Forms.BindingNavigator>

- 資料的物件標記法, 例如要在展示層中使用的[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)實體類別。

展示層通常會使用服務參考 (例如, Visual Studio 應用程式[中的 Windows Communication Foundation 服務和 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ) 存取仲介層。 展示層不會直接存取資料層。 展示層會透過仲介層中的資料存取元件, 與資料層通訊。

## <a name="middle-tier"></a>中介層
*中介層*是展示層和資料層用來彼此通訊的層。 一般中介層元件包括下列各項:

- 商務邏輯, 例如商務規則和資料驗證。

- 資料存取元件和邏輯, 如下所示:

  - [Tableadapter](create-and-configure-tableadapters.md)和[dataadapter 和 datareader](/dotnet/framework/data/adonet/dataadapters-and-datareaders)。

  - 資料的物件表示, 例如[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)的實體類別。

  - 常見的應用程式服務, 例如驗證、授權和個人化。

下圖顯示 Visual Studio 中可用的功能和技術, 以及它們可能符合多層式應用程式仲介層的位置。

![中介層元件](../data-tools/media/ntiermid.png)中介層

中介層通常會使用資料連線來連接到資料層。 此資料連線通常會儲存在資料存取元件中。

## <a name="data-tier"></a>資料層
*資料層*基本上是儲存應用程式資料的伺服器 (例如, 執行 SQL Server 的伺服器)。

下圖顯示 Visual Studio 中可用的功能和技術, 以及可能適用于多層式架構應用程式資料層的位置。

![資料層元件](../data-tools/media/ntierdatatier.png)資料層

資料層無法直接從展示層中的用戶端存取。 相反地, 仲介層中的資料存取元件會用於簡報和資料層之間的通訊。

## <a name="help-for-n-tier-development"></a>適用于多層式開發的協助
下列主題提供使用多層式架構應用程式的相關資訊:

[將資料集和 TableAdapter 分成不同的專案](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[使用 LINQ to SQL 的多層式架構 (N-Tier) 和遠端應用程式](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>另請參閱

- [逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
