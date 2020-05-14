---
title: 字串長度的限制 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df6e068ba612d5e8876e4fa01fbc0751759d5a80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701482"
---
# <a name="restrictions-on-string-lengths"></a>對字串長度的限制
原始程式碼管理外掛程式 API 限制各種函數中使用的字串的長度。

## <a name="string-length-values"></a>字串長度值

|持續性|值|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> 長度不包括終止`null`。 其他具有"_SIZE"後綴而不是"_LEN"的常量確實包括終止`null`的空間。

|持續性|值|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
