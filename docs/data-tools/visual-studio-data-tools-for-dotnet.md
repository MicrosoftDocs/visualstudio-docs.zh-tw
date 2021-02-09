---
title: 適用于 .NET 的資料工具
description: 複習 Visual Studio data tools for .NET，其提供 API 和工具支援以連接到資料庫、在記憶體中建立資料模型，以及在 UI 中顯示資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: f0a9609a578deb0c7c1b39a43f45b796b66a55ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858211"
---
# <a name="visual-studio-data-tools-for-net"></a>適用於 .NET 的 Visual Studio Data Tools

Visual Studio 和 .NET 一起提供廣泛的 API 和工具支援，以連接到資料庫、將記憶體中的資料模型化，以及在使用者介面中顯示資料。 提供資料存取功能的 .NET 類別稱為 [ADO.NET](/dotnet/framework/data/adonet/index)。 ADO.NET 和 Visual Studio 中的資料工具的設計主要是為了支援關係資料庫和 XML。 這些天、許多 NoSQL 資料庫廠商或協力廠商提供 ADO.NET 的提供者。

除了資料集及其相關類型以外， [.Net Core](/dotnet/core/)也支援 ADO.NET。 如果您是以 .NET Core 為目標，且需要 (ORM) 層的物件關聯式對應，請使用 [Entity Framework Core](/ef/core/)。

下圖顯示基本架構的簡化觀點：

![ADO.NET 架構](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>一般工作流程

一般工作流程如下：

1. 在本機電腦上安裝開發或測試資料庫。 請參閱 [安裝資料庫系統、工具和範例](../data-tools/installing-database-systems-tools-and-samples.md)。 如果您使用 Azure 資料服務，則不需要此步驟。

2. 測試 Visual Studio 中) 資料庫 (或服務或本機檔案的連接。 請參閱 [新增連接](../data-tools/add-new-connections.md)。

3.  (選擇性) 使用工具來產生及設定新的模型。 以 Entity Framework 為基礎的模型是新應用程式的預設建議。 無論您使用哪一個模型，它都是應用程式所互動的資料來源。 模型在邏輯上是在資料庫或服務和應用程式之間。 請參閱 [加入新的資料來源](../data-tools/add-new-data-sources.md)。

4. 將資料來源從 [ **資料來源** ] 視窗拖曳到 Windows Forms、ASP.NET 或 Windows Presentation Foundation 設計介面上，以產生資料系結程式碼，以您指定的方式將資料顯示給使用者。 請參閱 [將控制項系結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

5. 針對商務規則、搜尋和資料驗證等專案加入自訂程式碼，或利用基礎資料庫所公開的自訂功能。

您可以略過步驟3，並程式設計 .NET 應用程式，將命令直接發出至資料庫，而不是使用模型。 在此情況下，您會發現相關文件： [ADO.NET](/dotnet/framework/data/adonet/index)。 請注意，當您在記憶體中填入您自己的物件，然後將 UI 控制項資料系結至這些物件時，您仍然可以使用「 **資料來源設定向導** 」和「設計工具」來產生資料系結程式碼。

## <a name="see-also"></a>另請參閱

- [使用 Visual Studio 存取資料](../data-tools/accessing-data-in-visual-studio.md)
