---
title: 缺少連接屬性
description: 應用程式設定檔案中的連接屬性遺漏或不正確。 查看此 Visual Studio O/R 設計工具訊息的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 77724510-ff59-4d43-b933-a0434e1ac597
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 3e1c07424c4d43c9a3f545bd8c4d16ed5de726c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866485"
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>應用程式設定檔中的連接屬性遺漏或不正確

應用程式設定檔案中的連接屬性遺漏或不正確。 改用來自 *.dbml* 檔案的連接字串代替。

*.dbml* 檔案包含對應用程式設定檔中無法找到之連接字串的參考。 這是告知性訊息，當您按一下 [確定] 時就會建立連接字串設定。

若要回應這則訊息，請選取 **[確定]**。 *.Dbml* 檔中所包含的連接資訊會加入至應用程式設定。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
