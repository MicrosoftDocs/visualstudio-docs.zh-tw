---
title: 擴展專案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14108a304cc5f85c9a870bc66804df7daa98f3ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711756"
---
# <a name="extend-projects"></a>延伸項目
專案和解決方案是 Visual Studio 將代碼和資源檔組織到編譯和部署單元中的方式。 您可以在[專案(可視化工作室 SDK)](../extensibility/extending-projects.md)中找到有關專案的詳細資訊。

 您可以使用 Visual Studio SDK 和專案的託管包框架創建自己的項目類型,您可以在[專案的託管包框架](https://github.com/tunnelvisionlabs/MPFProj10)中下載。 要瞭解如何實施自定義專案,請參閱[新專案生成:引擎蓋下、第一部分](../extensibility/internals/new-project-generation-under-the-hood-part-one.md)和新[專案生成:在引擎蓋下,第二部分](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)。

 本節中的主題介紹如何創建自定義專案以及如何管理不同類型的 Visual Studio 解決方案。

## <a name="in-this-section"></a>本節內容
- [建立基本項目系統,第 1 部分](../extensibility/creating-a-basic-project-system-part-1.md)描述如何創建自定義項目系統。

- [建立基本項目系統,第 2 部分](../extensibility/creating-a-basic-project-system-part-2.md)描述如何創建自定義項目系統。

- [儲存資料檔案](../extensibility/saving-data-in-project-files.md)說明如何添加到專案<em>(。</em>proj_) 檔。

- [在執行時驗證項目的子型態](../extensibility/verifying-subtypes-of-a-project-at-run-time.md)說明如何在運行時驗證專案的子類型。

- [新增與移除屬性頁](../extensibility/adding-and-removing-property-pages.md)說明如何自定義自定義項目的屬性頁。

- [新增屬性到項目項目](../extensibility/adding-an-attribute-to-a-project-item.md)說明如何向自定義專案項添加屬性。

- [保留項目項目的屬性](../extensibility/persisting-the-property-of-a-project-item.md)說明如何保留自定義專案項的屬性。

- [管理通用 Windows 專案](../extensibility/managing-universal-windows-projects.md)說明如何管理通用專案。
