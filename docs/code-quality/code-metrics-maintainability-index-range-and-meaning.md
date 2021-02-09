---
title: 程式碼度量-可維護性索引範圍和意義
ms.date: 1/8/2021
description: 瞭解 Visual Studio 中程式碼度量的可維護性索引範圍度量。
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa825b439b75606da136635d5816ac3e19ea8392
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860460"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>程式碼度量-可維護性索引範圍和意義

問題：可維護性索引已重設為介於0到100之間。 這是怎麼做呢？

原先的度量計算方式如下： `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

使用此公式表示它的範圍是從171到未系結的負數。  當程式碼比起至0時，很難維護程式碼，而程式碼0和某些負值之間的差異並不實用。  由於負數的實用性，以及想要盡可能將計量維持在最少的情況下，我們決定將所有0或更少的索引視為0，然後將171或更少的範圍從0重定為0到100。 基於這個理由，我們使用的公式是：

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

除此之外，我們也決定保守臨界值。  想要的是，如果索引顯示為紅色，則我們會說出程式碼發生問題的高度信賴度。  這會給予我們下列閾值：

針對臨界值，我們決定將此0-100 範圍的80-20 細分為較低的雜訊層級，而且我們只會標示可疑的程式碼。 我們已使用下列閾值：

- 0-9 = 紅色
- 10-19 = 黃色
- 20-100 = 綠色
