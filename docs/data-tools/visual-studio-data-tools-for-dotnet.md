---
title: 適用於.NET 的 visual Studio 資料工具 |Microsoft 文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: b855516e6eb440b970489c3ebc6209dc0573f231
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-data-tools-for-net"></a>適用於.NET 的 visual Studio 資料工具

Visual Studio 和.NET Framework 一起提供廣泛的應用程式開發介面和工具支援連接至資料庫、 在記憶體中，資料模型化和使用者介面中顯示的資料。 .NET Framework 類別，可讓資料存取功能稱為[ADO.NET](/dotnet/framework/data/adonet/index)。 ADO.NET 中，以及資料的工具在 Visual Studio 中，原先設計主要是支援關聯式資料庫和 XML。 這幾天，許多 NoSQL 資料庫廠商或第三方提供 ADO.NET 提供者。

[.NET core](/dotnet/core/)支援 ADO.NET 資料集和相關的類型除外。 如果您的目標.NET Core 和需要的物件關聯式對應 (ORM) 層級，使用[Entity Framework Core](/ef/core/)。

下圖顯示基本架構的簡化的檢視：

![ADO.NET 架構](../data-tools/media/raddata-ado-net-architecture-diagram.png)

這是一般的工作流程：

1. 在本機電腦上安裝開發或測試資料庫。 請參閱[安裝資料庫系統、 工具和範例](../data-tools/installing-database-systems-tools-and-samples.md)。 如果您使用 Azure 資料服務時，不需要此步驟。

2. 在 Visual Studio 中測試的資料庫 （或服務或本機檔案） 的連接。 請參閱[加入新連接](../data-tools/add-new-connections.md)。

3. （選擇性）您可以使用工具來產生並設定新的模型。 Entity Framework 為基礎的模型是新的應用程式中提供預設建議。 模型中，您使用，一個是應用程式與互動的資料來源。 模型邏輯位於資料庫或服務和應用程式。 請參閱[加入新的資料來源](../data-tools/add-new-data-sources.md)。

4. 拖曳的資料來源**資料來源**視窗拖曳至 Windows Form、 ASP.NET 或 Windows Presentation Foundation 的設計介面，以產生會顯示您指定的方式中的使用者資料的資料繫結程式碼。 請參閱[控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

5. 加入自訂程式碼的事情，像是商務規則、 搜尋和資料驗證，或若要充分利用基礎資料庫會公開的自訂功能。

您可以略過步驟 3 和.NET 應用程式到問題的命令，直接以資料庫，而不是使用模型進行程式設計。 在此情況下，您可以在這裡找到相關文件： [ADO.NET](/dotnet/framework/data/adonet/index)。 請注意，您仍然可以使用之資料來源組態精靈和設計工具來產生資料繫結程式碼，當您填入您自己的記憶體，然後將 UI 控制項資料繫結至這些物件的物件。

## <a name="see-also"></a>另請參閱

- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)