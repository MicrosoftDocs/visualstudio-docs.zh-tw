---
title: 視覺化檢視安全性考慮 |Microsoft Docs
description: Visual Studio 偵錯工具的視覺化程式必須以完全信任的方式執行。 當您撰寫自己的時，請留意可能的安全性威脅，並採取適當的預防措施。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c735fe4a14a0412fbb41b28b5a40e27083c3bca6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884191"
---
# <a name="visualizer-security-considerations"></a>視覺化檢視安全性考量
撰寫視覺化檢視必須承擔可能的安全性威脅。 這些潛在的威脅目前沒有已知的傷害行為，但開發人員仍應暸解這些威脅，並採取本節中所說明的適當安全性考量，以對抗未來的威脅傷害。

 偵錯工具視覺化檢視需要比部分信任應用程式所允許還要大的權限。 當您在部分信任的程式碼中被停止時，視覺化檢視將不會載入。 若要使用視覺化檢視進行偵錯，您必須以完全信任方式執行程式碼。

## <a name="possible-malicious-debuggee-component"></a>可能有惡意的偵錯項目元件
 視覺化檢視是由至少兩個類別所組成：一個在偵錯工具端而另一個在偵錯項目端。 視覺化檢視通常會部署在放置於特殊目錄的不同組件中，但是也可以從偵錯項目外載入。 當發生這種情況時，偵錯工具會從偵錯項目取出程式碼，並且在偵錯工具中以完全信任方式執行。

 當偵錯項目並非為完全信任時，以完全信任執行偵錯項目端的程式碼就會變得有問題。 如果視覺化檢視嘗試從偵錯項目將部分信任組件載入偵錯工具，Visual Studio 將會結束視覺化檢視。

 但是，仍然存在次要弱點。 偵錯項目端能夠與從其他來源載入 (而非偵錯項目) 的偵錯工具端產生關聯。 偵錯項目端就能夠通知信任的偵錯工具端自行執行動作。 如果信任的偵錯工具端類別會公開像是 "delete this file" 的機制，則部分信任的偵錯項目就能夠在使用者叫用其視覺化檢視時叫用此機制。

 若要減輕這項弱點，請留意視覺化檢視所公開的介面。

## <a name="see-also"></a>另請參閱
- [視覺化架構](../debugger/visualizer-architecture.md)
- [如何：撰寫視覺化檢視](create-custom-visualizers-of-data.md)
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)