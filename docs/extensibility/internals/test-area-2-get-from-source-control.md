---
title: 測試區域2：從原始檔控制取得 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca98c927209062d2a1fc67c309d2f32c18d1b5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722575"
---
# <a name="test-area-2-get-from-source-control"></a>測試區域 2︰從原始檔控制中取得
此測試區域涵蓋從版本存放區透過 Get 命令抓取專案的測試案例。 這些測試案例可以同時套用至本機和 Web 專案。

## <a name="command-menu-access"></a>命令功能表存取
 下列 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的整合式開發環境功能表路徑用於測試案例中。

##### <a name="get-latest-version"></a>取得最新版本：

- [檔案]、[**原始檔控制** **]、[** **取得最新版本**]。

- 檔案，**取得最新版本**。

- 快捷方式功能表，**取得最新版本**。

- Get：**檔案**、**原始檔控制**、 **get**。

## <a name="expected-behavior"></a>預期的行為

##### <a name="get-latest-version"></a>取得最新版本：
 執行版本存放區中最新版本專案的無訊息（無 UI）抓取。

##### <a name="get"></a>獲取：
 顯示 [**取得**] 對話方塊，並允許使用者變更將抓取的檔案集，以及修改會影響檔案抓取方式的選項。

## <a name="test-cases"></a>測試案例

|動作|測試步驟|要驗證的預期結果|
|------------|----------------|--------------------------------|
|取得不存在於本機之檔案的最新版本|1. 建立專案。<br />2. 將專案新增至專案。<br />3. 將專案放在原始檔控制之下。<br />4. 刪除專案的本機複本。<br />5. 取得專案的最新版本（快捷方式功能表，**取得最新版本**）。|專案檔會在本機抓取。|
|取得不存在於本機的檔案|1. 建立專案。<br />2. 將專案新增至專案。<br />3. 將專案放在原始檔控制之下。<br />4. 刪除專案的本機複本。<br />5. 取得專案（[檔案]、[**原始檔控制** **]、[** **取得**\<item] >）。|專案檔會在本機抓取。|
|取得已獨佔簽出並在本機修改的檔案|1. 建立專案。<br />2. 將專案新增至專案。<br />3. 將專案放在原始檔控制之下。<br />4. 以獨佔方式簽出項目專案。<br />5. 修改本機複本。<br />6. 取得最新版本的專案（**File**，**取得最新版本的**\<item >）。 如果此步驟成功，請繼續進行下一個步驟。<br />7. 按一下 [警告] 對話方塊中的 [**取代**] 按鈕。|**從步驟 6 `:` ReResult**<br /><br /> 警告對話方塊指出檔案已簽出。<br /><br /> **步驟7中的 ReResult：**<br /><br /> 修改過的本機檔案會由版本存放區中的原始版本所取代。<br /><br /> 檔案為讀取/寫入。|
|取得和取代本機簽出、共用和修改的檔案|1. 建立新的專案。<br />2. 將專案新增至專案。<br />3. 將專案放在原始檔控制之下。<br />4. 將專案專案簽出為共用。<br />5. 修改本機複本。<br />6. 取得最新版本的專案（**File**，**取得最新版本的**\<item >）。 如果此步驟成功，請繼續進行下一個步驟。<br />7. 按一下 [警告] 對話方塊中的 [**取代**]。|**步驟6的結果：**<br /><br /> 警告對話方塊指出檔案已簽出。<br /><br /> **步驟7的結果：**<br /><br /> 修改過的本機檔案會由版本存放區中的原始版本所取代。<br /><br /> 檔案為讀取/寫入。|
|取得存在於本機的檔案，與版本存放區中的最新版本相同|1. 建立新的專案。<br />2. 將專案新增至專案。<br />3. 將專案放在原始檔控制之下。<br />4. 取得專案（[檔案]、[**原始檔控制** **]、[** **取得**\<item] >）。|本機檔案不變。|
|取得包含一個專案的解決方案|1. 建立包含一個專案的方案。<br />2. 將解決方案放在原始檔控制之下。<br />3. 刪除本機上的所有專案檔案。<br />4. 取得**解決方案（檔案**、**原始檔控制**、**取得**）。|所有已刪除的檔案都會在本機還原。|

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)