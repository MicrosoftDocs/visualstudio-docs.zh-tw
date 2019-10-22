---
title: 適用于 .NET 的資料工具
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 224fef3a02a2441553728a9a75fc5f9c456081a1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648096"
---
# <a name="visual-studio-data-tools-for-net"></a>適用於 .NET 的 Visual Studio Data Tools

Visual Studio 和 .NET 一起提供廣泛的 API 和工具支援，以便連接到資料庫、在記憶體中建立資料模型，以及在使用者介面中顯示資料。 提供資料存取功能的 .NET 類別稱為[ADO.NET](/dotnet/framework/data/adonet/index)。 ADO.NET 和 Visual Studio 中的資料工具，主要是為了支援關係資料庫和 XML 而設計的。 這幾天、許多 NoSQL 資料庫廠商或協力廠商都提供 ADO.NET 提供者。

[.Net Core](/dotnet/core/)支援 ADO.NET，但資料集和其相關類型除外。 如果您的目標是 .NET Core，而且需要物件關聯式對應（ORM）層，請使用[Entity Framework Core](/ef/core/)。

下圖顯示基本架構的簡單觀點：

![ADO.NET 架構](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>一般工作流程

一般工作流程如下：

1. 在您的本機電腦上安裝開發或測試資料庫。 請參閱[安裝資料庫系統、工具和範例](../data-tools/installing-database-systems-tools-and-samples.md)。 如果您使用 Azure 資料服務，則不需要執行此步驟。

2. 在 Visual Studio 中，測試與資料庫（或服務或本機檔案）的連接。 請參閱[新增連接](../data-tools/add-new-connections.md)。

3. 選擇性使用工具來產生和設定新的模型。 以 Entity Framework 為基礎的模型是新應用程式的預設建議。 無論您使用哪一種模型，都是應用程式互動的資料來源。 模型在資料庫或服務與應用程式之間的邏輯上。 請參閱[加入新的資料來源](../data-tools/add-new-data-sources.md)。

4. 將資料來源從 [**資料來源**] 視窗拖曳至 [Windows Forms]、[ASP.NET] 或 [Windows Presentation Foundation] 設計介面上，以產生資料系結程式碼，以您指定的方式將資料顯示給使用者。 請參閱[將控制項系結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

5. 新增商務規則、搜尋和資料驗證等專案的自訂程式碼，或利用基礎資料庫所公開的自訂功能。

您可以略過步驟3並程式設計 .NET 應用程式，直接將命令發行至資料庫，而不是使用模型。 在此情況下，您會發現相關文件： [ADO.NET](/dotnet/framework/data/adonet/index)。 請注意，當您在記憶體中填入自己的物件，然後將 UI 控制項資料系結至這些物件時，您仍然可以使用**資料來源設定 Wizard**和設計工具來產生資料系結程式碼。

## <a name="see-also"></a>請參閱

- [使用 Visual Studio 存取資料](../data-tools/accessing-data-in-visual-studio.md)