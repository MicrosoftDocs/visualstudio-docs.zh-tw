---
title: 測試區域2：從原始檔控制取得 |Microsoft Docs
description: 此測試區域涵蓋使用 Get 從版本存放區中取出專案的測試案例。 這些測試案例可以同時套用至本機和 Web 專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab6a35aa896d7a68e151007d6f694672f7477688
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073426"
---
# <a name="test-area-2-get-from-source-control"></a>測試區域 2：從原始檔控制取得
此測試區域涵蓋可透過 Get 命令從版本存放區中取得專案的測試案例。 這些測試案例可以同時套用至本機和 Web 專案。

## <a name="command-menu-access"></a>命令功能表存取
 下列 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境功能表路徑用於測試案例中。

##### <a name="get-latest-version"></a>取得最新版本：

- 檔案、**原始檔控制**、**取得最新版本**。

- 檔案，**取得最新版本**。

- 快速鍵功能表， **取得最新版本**。

- Get： **File**、 **Source Control**、 **get**。

## <a name="expected-behavior"></a>預期行為

##### <a name="get-latest-version"></a>取得最新版本：
 執行無提示 (沒有 UI) 從版本存放區抓取專案的最新版本。

##### <a name="get"></a>取得：
 顯示 [ **取得** ] 對話方塊，並允許使用者對將抓取的檔案集進行變更，以及修改影響檔案取出方式的選項。

## <a name="test-cases"></a>測試案例

|動作|測試步驟|要驗證的預期結果|
|------------|----------------|--------------------------------|
|取得不存在於本機的檔案最新版本|1. 建立專案。<br />2. 將專案加入至專案。<br />3. 將專案放在原始檔控制之下。<br />4. 刪除專案的本機複本。<br />5. 取得專案 (快捷方式功能表的最新版本，) **取得最新版本** 。|專案檔會在本機取出。|
|取得不存在於本機的檔案|1. 建立專案。<br />2. 將專案加入至專案。<br />3. 將專案放在原始檔控制之下。<br />4. 刪除專案的本機複本。<br />5. **取得 (檔案**、原始檔 **控制**、 **取得** \<item>) 的專案。|專案檔會在本機取出。|
|取得以獨佔方式簽出並在本機修改的檔案|1. 建立專案。<br />2. 將專案加入至專案。<br />3. 將專案放在原始檔控制之下。<br />4. 以獨佔方式簽出項目專案。<br />5. 修改本機複本。<br />6. 取得 **專案 (的** 最新版本， **取得最新版本的** \<item>) 。 如果此步驟成功，請繼續下一個步驟。<br />7. 按一下警告對話方塊中的 [ **取代** ] 按鈕。|**步驟6中的 ReResult**`:`<br /><br /> 警告對話方塊指出檔案已簽出。<br /><br /> **步驟7中的 ReResult：**<br /><br /> 已修改的本機檔案會由版本存放區中的原始版本取代。<br /><br /> 檔案為讀取/寫入。|
|取得和取代在本機簽出、共用和修改的檔案|1. 建立新專案。<br />2. 將專案加入至專案。<br />3. 將專案放在原始檔控制之下。<br />4. 將專案專案簽出為共用。<br />5. 修改本機複本。<br />6. 取得 **專案 (的** 最新版本， **取得最新版本的** \<item>) 。 如果此步驟成功，請繼續下一個步驟。<br />7. 按一下警告對話方塊中的 [ **取代** ]。|**步驟6的結果：**<br /><br /> 警告對話方塊指出檔案已簽出。<br /><br /> **步驟7的結果：**<br /><br /> 已修改的本機檔案會由版本存放區中的原始版本取代。<br /><br /> 檔案為讀取/寫入。|
|取得存在於本機的檔案，與版本存放區中的最新版本相同|1. 建立新專案。<br />2. 將專案加入至專案。<br />3. 將專案放在原始檔控制之下。<br />4. **取得 (檔案**、原始檔 **控制**、 **取得** \<item>) 的專案。|本機檔案未變更。|
|取得具有一個專案的解決方案|1. 建立具有一個專案的方案。<br />2. 將方案放置在原始檔控制之下。<br />3. 刪除本機上的所有專案檔。<br />4. 取得 **方案 (檔案**、 **原始檔控制**、 **取得**) 。|所有已刪除的檔案都會在本機還原。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
