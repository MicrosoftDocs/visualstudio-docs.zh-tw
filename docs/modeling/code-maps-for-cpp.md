---
title: 查看 c + + 原始檔和標頭檔之間的相依性
description: 提供 c + + 專案的 code map 相關資訊。
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93ac1f7364e23ef9ed2b44ecd1c536a7ab2b3d40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389666"
---
# <a name="code-maps-for-c-projects"></a>C + + 專案的 Code map

如果要為 C++ 專案建立更完整的對應，請在這些專案上設定瀏覽資訊編譯器選項 (**/FR**)。 否則會出現訊息並提示您設定此選項。 如果選取 [確定] ，則只會為目前的對應設定這個選項。 您可以選擇隱藏所有之後對應的訊息。

當您開啟包含 Visual C++ 專案的方案時，更新 IntelliSense 資料庫可能需要一些時間。 在這段期間，您可能無法建立標頭 (*.h* 或) 檔案的 code map， `#include` 直到 IntelliSense 資料庫完成更新為止。 您可以在 Visual Studio 狀態列中監視更新進度。

- 若要查看方案中所有原始程式檔與標頭檔之間的相依性，請選取 [**架構**  >  **產生 Include 檔圖形]**。

   ![機器碼相依性圖形](../modeling/media/dependencygraphgeneral_nativecode.png)

- 若要查看目前開啟的檔案與相關原始程式檔和標頭檔之間的相依性，請開啟原始程式檔或標頭檔。 在檔案內的任意處開啟檔案捷徑功能表。 選擇 [產生 Include 檔圖形] 。

   ![.h 檔案的第一層相依性圖形](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>針對 C 和 c + + 程式碼的 code map 進行疑難排解

C 和 C++ 程式碼不支援下列項目：

- 基底類型不會出現在包含父代階層架構的對應中。

- 大部分的 [顯示]  功能表項目無法供 C 和 C++ 程式碼使用。

當您建立 C 和 c + + 程式碼的 code map 時，可能會發生下列問題：

|**問題**|**可能的原因**|**解決方法**|
|-|-|-|
|無法產生 Code Map。|方案中沒有成功建立的專案。|修正發生的建置錯誤，然後重新產生對應。|
|當您嘗試從 [ **架構** ] 功能表產生 code map 時，Visual Studio 會變成沒有回應。|程式資料庫 (.pdb) 檔案可能會損毀。<br /><br /> .pdb 檔案會儲存偵錯資訊，例如類型、方法和原始程式檔資訊。|重建方案後再試一次。|
|IntelliSense 瀏覽資料庫的某些設定已停用。|某些 IntelliSense 設定可能會在 [Visual Studio **選項** ] 對話方塊中停用。|開啟這些設定來加以啟用。<br /><br /> 請參閱 [選項、文字編輯器、C/c + +、Advanced](../ide/reference/options-text-editor-c-cpp-advanced.md)。|
|[未知方法]  訊息出現在方法節點上。<br /><br /> 發生這個問題是因為無法解析方法的名稱。|二進位檔可能沒有基底重新配置表格。|在連結器中開啟 **/FIXED:NO** 選項。|
||程式資料庫 (.pdb) 檔案可能無法建置。<br /><br /> .pdb 檔案會儲存偵錯資訊，例如類型、方法和原始程式檔資訊。|在連結器中開啟 **/DEBUG** 選項。|
||無法在預期的位置中開啟或找到 .pdb 檔案。|請確定預期的位置中有 .pdb 檔案存在。|
||已從 .pdb 檔案中移除偵錯資訊。|如果在連結器中使用 **/PDBSTRIPPED** 選項，請改為包含完整的 .pdb 檔案。|
||呼叫端不是函式，而且為二進位檔案中的 Thunk 或資料區段中的指標。|當呼叫端為 Thunk 時，請嘗試使用 `_declspec(dllimport)` 來避免 Thunk。|

## <a name="see-also"></a>另請參閱

- [使用 code map 對應相依性](../modeling/map-dependencies-across-your-solutions.md)
