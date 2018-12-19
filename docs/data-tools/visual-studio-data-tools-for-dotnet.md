---
title: 適用於.NET 的資料工具
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: bf28747e8bd111767fbe314cbb658a38ef059ae2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066336"
---
# <a name="visual-studio-data-tools-for-net"></a>適用於 .NET 的 Visual Studio Data Tools

Visual Studio 和.NET Framework 一起提供廣泛的 API 和工具連線到資料庫、 模型化資料在記憶體中，以及在使用者介面中顯示資料的支援。 .NET Framework 類別提供資料存取功能，稱為[ADO.NET](/dotnet/framework/data/adonet/index)。 ADO.NET，以及工具在 Visual Studio 中的資料已設計為支援關聯式資料庫和 XML。 如今，許多 NoSQL 資料庫廠商或第三方，會提供 ADO.NET 提供者。

[.NET core](/dotnet/core/)支援 ADO.NET 資料集和相關的類型除外。 如果您以.NET Core 為目標，而且需要的物件關聯式對應 (ORM) 層級，使用[Entity Framework Core](/ef/core/)。

下圖顯示簡單的檢視的基本架構：

![ADO.NET 架構](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>一般工作流程

典型的工作流程如下：

1. 在本機電腦上安裝開發或測試資料庫。 請參閱[安裝資料庫系統、 工具和範例](../data-tools/installing-database-systems-tools-and-samples.md)。 如果您使用 Azure 資料服務，就不需要此步驟。

2. 在 Visual Studio 中測試資料庫 （或服務或本機檔案） 的連線。 請參閱[新增連線](../data-tools/add-new-connections.md)。

3. （選擇性）您可以使用工具來產生和設定新的模型。 Entity Framework 為基礎的模型是新的應用程式提供預設建議。 模型中，您使用，一個是與應用程式互動的資料來源。 模型會以邏輯方式位於資料庫或服務與應用程式。 請參閱[加入新的資料來源](../data-tools/add-new-data-sources.md)。

4. 拖曳的資料來源**Zdroje dat**視窗拖曳至 Windows Form、 ASP.NET 或 Windows Presentation Foundation 的設計介面，以產生資料繫結程式碼，會在您指定的方法中對使用者顯示的資料。 請參閱[控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

5. 新增項目，例如商務規則、 搜尋、 資料驗證，或利用基礎資料庫公開 （expose） 的自訂功能的自訂程式碼。

您可以略過步驟 3 和程式的.NET 應用程式，以發出命令，直接與資料庫，而不是使用模型。 在此情況下，您會發現相關文件： [ADO.NET](/dotnet/framework/data/adonet/index)。 請注意，您仍然可以使用**資料來源組態精靈**和設計工具來產生資料繫結程式碼，當您填入自己的記憶體，然後將 UI 控制項資料繫結至這些物件的物件。

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio 存取資料](../data-tools/accessing-data-in-visual-studio.md)