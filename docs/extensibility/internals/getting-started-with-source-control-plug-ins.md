---
title: 具有原始檔控制外掛程式的消費者入門 |Microsoft Docs
description: 瞭解如何建立原始檔控制外掛程式，該外掛程式會執行原始檔控制外掛程式 API 中所定義的函式，以便在原始程式碼版本控制中使用。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1524e4c4f08b272fd17973597d558efdabec41af
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480495"
---
# <a name="get-started-with-source-control-plug-ins"></a>開始使用原始檔控制外掛程式
若要建立原始檔控制外掛程式，您必須建立可執行原始檔控制外掛程式 API 中所定義之函式的 DLL，然後向註冊 DLL， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使其可在原始程式碼版本控制中使用。

 有三個版本的原始檔控制外掛程式 API (版本1.1、1.2 和 1.3) 適用于原始檔控制外掛程式。此處所記載的原始檔控制外掛程式 API 是版本1.3。 其設計目的是要與支援1.1 和1.2 版的原始檔控制外掛程式完全相容。 [原始檔控制外掛程式 api 1.3 版的新](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)功能一節將詳細說明最新版原始檔控制外掛程式 api 所支援的新功能。

## <a name="in-this-section"></a>本節內容
- [如何：安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 描述如何建立插入原始檔控制 DLL 所需的登錄專案。

- [原始檔控制外掛程式 API 版本1.3 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 提供在版本1.3 中對原始檔控制外掛程式 API 所做變更的簡短總覽。

- [原始檔控制外掛程式 API 版本1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 提供在版本1.2 中對原始檔控制外掛程式 API 所做變更的簡短總覽。

## <a name="related-sections"></a>相關章節
- [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)

 提供原始檔控制外掛程式 API 中所有元素的完整清單。

- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)

 定義原始檔控制外掛程式 SDK 並說明包含的資源。
