---
title: XSLT 預設範本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bb4351d6b95c7aee929274135454ecf7aa91574
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669330"
---
# <a name="xslt-default-templates"></a>XSLT 預設範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在樣式表中沒有相符的明確範本規則時，在 XSLT 處理期間會使用預設範本。 預設範本 (也就是內建的範本規則) 是在 W3C XSLT 1.0 建議事項的 5.8 節定義的。 即使沒有相符的明確範本規則，預設範本還是可以讓 XSLT 處理器處理節點。 但是，在樣式表中不會明確地定義內建的範本規則，因此，這可能會造成非預期或令人混淆的 XSLT 轉換結果。

 XSLT 偵錯工具現在會顯示 XSLT 預設範本的程式碼。 當您逐步執行 XSLT 轉換時，如果使用預設範本，偵錯工具會在視窗中顯示預設範本。 這可讓您逐步執行預設範本的程式碼，並在其指令上設定中斷點。

## <a name="see-also"></a>另請參閱
 [偵錯 XSLT](../xml-tools/debugging-xslt.md)
