---
title: XSLT 預設範本
description: 瞭解樣式表單中沒有相符的明確範本規則時，在 XSLT 處理期間使用的 XSLT 預設範本。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 74b4cfebc7a6160577f1e817c9171f2eae69533c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874752"
---
# <a name="xslt-default-templates"></a>XSLT 預設範本

在樣式表中沒有相符的明確範本規則時，在 XSLT 處理期間會使用預設範本。 預設範本 (也就是內建的範本規則) 是在 W3C XSLT 1.0 建議事項的 5.8 節定義的。 即使沒有相符的明確範本規則，預設範本還是可以讓 XSLT 處理器處理節點。 但是，在樣式表中不會明確地定義內建的範本規則，因此，這可能會造成非預期或令人混淆的 XSLT 轉換結果。

XSLT 偵錯工具現在會顯示 XSLT 預設範本的程式碼。 當您逐步執行 XSLT 轉換時，如果使用預設範本，偵錯工具會在視窗中顯示預設範本。 這可讓您逐步執行預設範本的程式碼，並在其指令上設定中斷點。

## <a name="see-also"></a>另請參閱

- [偵錯 XSLT](../xml-tools/debugging-xslt.md)
