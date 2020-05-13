---
title: 管理應用程式資源 (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e53c3701e31733c54869c71820956d674ed4fb8b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593690"
---
# <a name="manage-application-resources-net"></a>管理應用程式資源 (.NET)

資源檔案是屬於應用程式的一部分，但不會經過編譯的檔案，例如圖示檔案或音訊檔案。 由於這些檔案不屬於編譯處理程序的一部分，您可以變更它們而無需重新編譯二進位檔。 如果您打算將應用程式當地語系化，您應該針對所有字串和其他在將應用程式當地語系化時需要變更的資源使用資源檔。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[管理應用程式資源 (Visual Studio for Mac)](/visualstudio/mac/managing-app-resources)。

有關 .NET 桌面應用中的資源的詳細資訊，請參閱[桌面應用中的資源](/dotnet/framework/resources/index)。

## <a name="work-with-resources"></a>使用資源

在 受控碼專案中，開啟 [專案屬性] 視窗。 您可以透過下列方式開啟 [屬性] 視窗：

- 按右鍵**解決方案資源管理器**中的專案節點並選擇**屬性**
- 在 **Ctrl**+**Q** 搜尋方塊中，輸入**專案屬性**
- 在**解決方案資源管理器**中選擇**Alt**+**Enter**

選擇"**資源**"選項卡。如果專案不包含 *.resx*檔，則可以添加 .resx 檔，添加和刪除不同類型的資源，並修改現有資源。

## <a name="resources-in-other-project-types"></a>其他專案類型中的資源

.NET 專案管理資源的方式和其他專案類型不同。 如需下列資源的詳細資訊：

- 通用 Windows 平台 (UWP) 應用程式，請參閱[應用程式資源和資源管理系統](/windows/uwp/app-resources/)
- C++ 專案，請參閱[使用資源檔](/cpp/windows/working-with-resource-files)和[如何：建立資源](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>另請參閱

- [桌面應用中的資源（.NET 框架）](/dotnet/framework/resources/index)
- [管理應用程式資源 (Visual Studio for Mac)](/visualstudio/mac/managing-app-resources)
