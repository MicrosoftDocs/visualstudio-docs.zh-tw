---
title: 開始使用原始碼管理外掛程式 。微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efc21e07830614d9d3041b2d2d231fd82c652114
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708338"
---
# <a name="get-started-with-source-control-plug-ins"></a>開始使用原始碼管理外掛程式
要建立原始程式碼管理外掛程式,必須建立一個 DLL,該 DLL 實現原始碼管理外掛程式 API 中定義[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的函數,然後註冊 DLL 使其可用於原始碼版本控制程式。

 原始程式碼管理外掛程式 API 的三個版本(版本 1.1、1.2 和 1.3)可用於原始程式碼管理外掛程式。此處記錄的原始程式碼管理外掛程式 API 是版本 1.3。 它設計為與支援版本 1.1 和 1.2 的原始程式碼管理外掛程式完全相容。 [原始程式碼管理外掛程式 API 版本 1.3 部分中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)詳細介紹了原始碼管理外掛程式 API 的最新版本中支援的新功能。

## <a name="in-this-section"></a>本節內容
- [如何:安裝原始碼管理外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 描述如何使註冊表項插入原始程式碼管理 DLL 所需的註冊表項。

- [原始程式碼管理外掛程式 API 版本 1.3 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 簡要概述對版本 1.3 中的原始程式碼管理外掛程式 API 所做的更改。

- [原始程式碼管理外掛程式 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 簡要概述對版本 1.2 中的原始程式碼管理外掛程式 API 所做的更改。

## <a name="related-sections"></a>相關章節
- [原始程式管理外掛程式](../../extensibility/source-control-plug-ins.md)

 提供原始程式碼管理外掛程式 API 中所有元素的完整清單。

- [建立原始碼管理外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)

 定義原始程式碼管理外掛程式 SDK 並描述包含的資源。
