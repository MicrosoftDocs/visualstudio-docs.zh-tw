---
title: 適用於受控碼的受控最小規則規則集
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 56d8528a5a419eb23b1192ef265f70ea536cfe48
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890439"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>適用於受控碼的受控最小規則規則集

受管理的最小規則的重點在於程式碼，包括潛在的安全性漏洞、 應用程式當機，以及其他重要的邏輯和設計錯誤中最關鍵的問題。 建立包含這個規則設定任何自訂規則集中您針對您的專案。

|規則|描述|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|具有可處置欄位的類型應該為可處置|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|必須移除空的完成項|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|可處置的欄位應該受到處置|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|在覆寫 ValueType.Equals 上多載等號運算子|
