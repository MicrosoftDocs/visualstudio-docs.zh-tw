---
title: ClickOnce 部署範例和逐步解說 |Microsoft Docs
description: 使用這些範例應用程式、範例程式碼和逐步解說解說，瞭解用來部署 Windows Forms、WPF 和主控台應用程式的技術。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- applications [Visual Studio], walkthroughs
- Visual Studio, deployment walkthroughs
- Visual Studio, walkthroughs
ms.assetid: 3973276b-7b11-4692-a0a2-32bebf0b9c2a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b8b3a1482a01f0fcef6a8a64fcb3ec0a0023850
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918315"
---
# <a name="clickonce-deployment-samples-and-walkthroughs"></a>ClickOnce 部署範例和逐步解說
本節包含範例應用程式、範例程式碼和逐步解說，說明用來部署 Windows Forms、WPF 和主控台應用程式的語法、結構和技術。

 範例程式碼適用于教學用途，不應該在未修改的情況下在部署的解決方案中使用。 尤其是，必須將安全性納入考慮。

## <a name="clickonce-deployment"></a>ClickOnce 部署

|主題|描述|
|-----------|-----------------|
|[手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|說明如何使用.NET Framework 公用程式，部署 ClickOnce 應用程式。|
|[使用 ClickOnce 部署 API 依需求下載元件](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|示範如何將應用程式中的特定元件標示為「選擇性」，以及如何使用命名空間中的類別來下載它們 <xref:System.Deployment.Application> 。|
|[使用設計工具以 ClickOnce 部署 API 隨選下載元件](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|說明如何只有在應用程式第一次使用應用程式組件時，才下載這些組件。|

## <a name="see-also"></a>另請參閱

- [Visual Studio 逐步解說](/previous-versions/szatc41e(v=vs.110))