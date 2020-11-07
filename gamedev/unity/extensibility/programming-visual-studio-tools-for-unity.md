---
title: Visual Studio Tools for Unity 程式設計 | Microsoft Docs
description: 請參閱使用 Visual Studio Tools for Unity (VSTU) API 的程式設計範例。 自訂 VSTU 所建立的專案檔。 與 VSTU 共用 Unity 記錄回呼。
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: c98a3cdbcece87ad5e8fbe0e91ae76f677494477
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341556"
---
# <a name="program-visual-studio-tools-for-unity"></a>使用 Visual Studio Tools for Unity 設計程式
在本節中，您將找到使用 Visual Studio Tools for Unity 應用程式開發介面的範例。

## <a name="examples"></a>範例
 以下是一些範例，示範如何使用 Visual Studio Tools for Unity 應用程式開發介面。

### <a name="customize-project-files-created-by-vstu"></a>自訂 VSTU 所建立的專案檔
 Visual Studio Tools for Unity 在專案檔產生期間提供 Unity 樣式回呼。 若要瞭解如何在每次重新產生專案檔時進行修改，請參閱 [範例：產生專案](./customize-project-files-created-by-vstu.md)檔。

### <a name="share-the-unity-log-callback-with-vstu"></a>與 VSTU 共用 Unity 記錄回呼
 Visual Studio Tools for Unity 使用 Unity 註冊記錄回呼，以便將其主控台串流至 Visual Studio。 如果您的編輯器指令碼也使用 Unity 註冊記錄回呼，VSTU 回呼可能會與這個回呼相衝突。 若要瞭解如何與 VSTU 共用 Unity 記錄回呼，請參閱 [範例：記錄回呼](./share-the-unity-log-callback-with-vstu.md)。
