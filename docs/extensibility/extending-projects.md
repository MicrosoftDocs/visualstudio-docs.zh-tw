---
title: 擴充專案 |Microsoft Docs
description: 瞭解如何在 Visual Studio SDK 中建立您自己的自訂專案類型，以及如何管理不同類型的 Visual Studio 解決方案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 997f4e32007af641b24ba933d2c891e447382786
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895826"
---
# <a name="extend-projects"></a>擴充專案
專案和解決方案是 Visual Studio 將程式碼和資源檔組織成編譯和部署單位的方式。 您可以在 [ (VISUAL STUDIO SDK) 的專案 ](../extensibility/extending-projects.md)中找到專案的詳細資訊。

 您可以使用 Visual Studio SDK 和適用于專案的 Managed 封裝架構來建立自己的專案類型，您可以在 [適用于專案的 Managed 封裝架構](https://github.com/tunnelvisionlabs/MPFProj10)中下載這些專案類型。 若要瞭解如何實行自訂專案，請參閱 [新的專案產生：在幕後，](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 第 [二部分和新專案產生：在幕後，第二部分](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 本節中的主題描述如何建立自訂專案，以及如何管理不同類型的 Visual Studio 方案。

## <a name="in-this-section"></a>本節內容
- [建立基本的專案系統，第1部分](../extensibility/creating-a-basic-project-system-part-1.md) 說明如何建立自訂專案系統。

- [建立基本的專案系統，第2部分](../extensibility/creating-a-basic-project-system-part-2.md) 說明如何建立自訂專案系統。

- [將資料儲存在專案檔案中](../extensibility/saving-data-in-project-files.md) 說明如何加入至專案 (<em>。</em>proj * ) 檔案。

- [在執行時間驗證專案的子類型](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) 說明如何在執行時間驗證專案的子類型。

- [新增和移除屬性頁](../extensibility/adding-and-removing-property-pages.md) 說明如何自訂自訂專案的屬性頁。

- [將屬性新增至專案專案](../extensibility/adding-an-attribute-to-a-project-item.md) 說明如何將屬性新增至自訂專案專案。

- [保存專案專案的屬性](../extensibility/persisting-the-property-of-a-project-item.md) 說明如何保存自訂專案專案的屬性。

- [管理通用 Windows 專案](../extensibility/managing-universal-windows-projects.md) 說明如何管理通用專案。
