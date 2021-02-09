---
title: 連接字串包含密碼
description: 連接字串包含具有純文字密碼的認證，並且不使用整合式安全性
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1ce11b59ad7f38de4c71fa13371da16225b5b843
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858406"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>連接字串包含具有純文字密碼的認證，並且不使用整合式安全性

是否要將連接字串連同這些敏感資訊一起儲存到目前的 DBML 檔案和應用程式組態檔？  按 [否] 只會儲存連接字串，而不會儲存敏感性資訊。

使用內含敏感資訊 (含在連接字串中的密碼) 的資料連接時，可以選擇是否在將連接字串儲存至專案的 DBML 檔案和應用程式組態檔時包含敏感資訊。

> [!WARNING]
> 將 [連線] 屬性的 [應用程式設定] 屬性明確設定為 [False]，會將密碼新增到 DBML 檔案中。

## <a name="save-options"></a>[儲存] 選項

- 若要儲存具有敏感性資訊的連接字串，請選擇 [ **是]**。

   連接字串會儲存為應用程式設定。 連接字串會包含純文字的敏感資訊。 DBML 檔案不包含敏感資訊。

- 若要儲存不含敏感性資訊的連接字串，請選擇 [ **否**]。

   連接字串會儲存為應用程式設定，但是不包含密碼。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
