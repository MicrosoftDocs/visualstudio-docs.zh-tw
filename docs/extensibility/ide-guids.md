---
title: IDE Guid |Microsoft Docs
description: VSConstants 類別會發行 IDE 某些部分的一組 Guid。 本文列出 Guid。
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- GUIDs, integrated development environment
- IDE, GUIDs
ms.assetid: d31a0f97-b7be-4fb5-a942-8ba4527bc068
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6351ea576c8976bd12fe206d8c4dbbe5f34a72d8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069851"
---
# <a name="ide-guids"></a>IDE GUID

類別會將 <xref:Microsoft.VisualStudio.VSConstants> 整合式開發環境中某些部分的 guid 發佈 (IDE) ，如下表所示。

## <a name="core-systems"></a>核心系統

|常數|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.HtmDocData_guid>|62C81794-A9EC-11D0-8198-00A0C91BBEE3|
|<xref:Microsoft.VisualStudio.VSConstants.VsPackageGuid.HtmlEditorPackage_guid>|1B437D20-F8FE-11D2-A6AE-00104BCC7269|
|<xref:Microsoft.VisualStudio.VSConstants.VsLanguageServiceGuid.HtmlLanguageService_guid>|58E975A0-F8FE-11D2-A6AE-00104BCC7269|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>|A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.SolutionItemsProject_guid>|D1DCDB85-C5E8-11d2-BFCA-00C04F990235|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.VsEnvironmentPackage_guid>|DA9FB551-C724-11d0-AE1F-00A0C90FFFC3|
|<xref:Microsoft.VisualStudio.VSConstants.VsEditorFactoryGuid.HtmlEditor_guid>|C76D83F8-A489-11D0-8195-00A0C91BBEE3|
|<xref:Microsoft.VisualStudio.VSConstants.VsEditorFactoryGuid.TextEditor_guid>|8B382828-6202-11d1-8870-0000F87579D2|

## <a name="broadly-visible-components"></a>廣泛可見的元件

|常數|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.VsUIHierarchyWindow_guid>|7D960B07-7AF8-11D0-8E5E-00A0C911005A|
|<xref:Microsoft.VisualStudio.VSConstants.VsEditorFactoryGuid.ExternalEditor_guid>|8137C9E8-35FE-4AF2-87B0-DE3C45F395FD|
|Microsoft.VisualStudio.VSConstants.SID_SUIHostCommandDispatcher|e69cd190-1276-11d1-9f64-00a0c911004f|
|Microsoft.VisualStudio.VSConstants.SID_SVsGeneralOutputWindowPane|65482c72-defa-41b7-902c-11c091889c83|

## <a name="files-virtual-and-physical-folders-and-subprojects"></a>檔案、虛擬和實體資料夾和子專案

|常數|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.ItemTypeGuid.PhysicalFile_guid>|6bb5f8ee-4483-11d3-8bcf-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.ItemTypeGuid.PhysicalFolder_guid>|6bb5f8ef-4483-11d3-8bcf-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.ItemTypeGuid.SubProject_guid>|EA6618E8-6E24-4528-94BE-6889FE16485C|
|<xref:Microsoft.VisualStudio.VSConstants.ItemTypeGuid.VirtualFolder_guid>|6bb5f8f0-4483-11d3-8bcf-00c04f8ec28c|

## <a name="ui-contexts"></a>UI 內容

|常數|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>|8fe2df1d-e0da-4ebe-9d5c-415d40e487b5|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>|adfc4e61-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>|adfc4e63-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>|b706f393-2e5b-49e7-9e2e-b1825f639b63|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>|adfc4e65-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>|adfc4e62-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>|adfc4e64-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>|adfc4e60-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>|f1536ef8-92ec-443c-9ed7-fdadf150da82|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>|93694fa0-0397-11d1-9f4e-00a0c911004f|
|<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>|adfc4e66-0397-11d1-9f4e-00a0c911004f|

## <a name="output-pane"></a>輸出窗格

|常數|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.BuildOutputPane_guid>|1BD8A850-02D1-11D1-BEE7-00A0C913D1F8|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.DebugPane_guid>|FC076020-078A-11D1-A7DF-00A0C9110051|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.GeneralPane_guid>|3C24D581-5591-4884-A571-9FE89915CD64|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.SortedBuildOutputPane_guid>|2032B126-7C8D-48AD-8026-0E0348004FC0|
|<xref:Microsoft.VisualStudio.VSConstants.OutputWindowPaneGuid.StoreValidationPane_guid>|54065C74-1B11-4249-9EA7-5540D1A6D528|
|Microsoft.VisualStudio.VSConstants.SID_SVsGeneralOutputWindowPane|65482c72-defa-41b7-902c-11c091889c83|

## <a name="command-sets-and-properties"></a>命令集和屬性

|常數|GUID|
|--------------|----------|
|Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97|5EFC7975-14BC-11CF-9B2B-00AA00573819|
|Microsoft.VisualStudio.VSConstants.GUID_VsUIHierarchyWindowCmds>|60481700-078b-11d1-aaf8-00a0c9055a90|

## <a name="iunknown"></a>IUnknown

|常數|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.IID_IUnknown>|00000000-0000-0000-C000-000000000046|

## <a name="task-list-guids"></a>工作清單 Guid

|常數|GUID|
|--------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.All>|1880202e-fc20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.CheckedTasks>|18802036-fc20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.CommentTasks>|18802034-fc20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.CompilerTasks>|18802033-fc20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.CurrentFileTasks>|18802035-fc20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.HTMLTasks>|36ac1c0d-fe86-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.ShortcutTasks>|18802030-fc20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.UncheckedTasks>|18802037-fc20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.VsTaskListView.UserTasks>|1880202f-fc20-11d2-8bb1-00c04f8ec28c|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.VsTaskList_guid>|BC5955D5-aa0d-11d0-a8c5-00a0c921a4d2|
|<xref:Microsoft.VisualStudio.VSConstants.VsPackageGuid.VsTaskListPackage_guid>|4A9B7E50-aa16-11d0-a8c5-00a0c921a4d2|

## <a name="component-selector-page-guids"></a>元件選取器頁面 Guid

|常數|GUID|
|---------------|----------|
|Microsoft.VisualStudio.VSConstants.GUID_COMClassicPage|9A341D96-5A64-11d3-BFF9-00C04F990235|
|Microsoft.VisualStudio.VSConstants.GUID_COMPlusPage|9A341D95-5A64-11d3-BFF9-00C04F990235|
|Microsoft.VisualStudio.VSConstants.GUID_SolutionPage|9A341D97-5A64-11d3-BFF9-00C04F990235|

## <a name="miscellaneous-shell-guids"></a>其他 shell Guid

|常數|GUID|
|---------------|----------|
|<xref:Microsoft.VisualStudio.VSConstants.CLSID.VsCfgProviderEventsHelper_guid>|99913f1f-1ee3-11d1-8a6e-00c04f682e21|
|<xref:Microsoft.VisualStudio.VSConstants.VsPackageGuid.VsDocOutlinePackage_guid>|21af45b0-ffa5-11d0-b63f-00a0c922e851|
|Microsoft.VisualStudio.VSConstants.SID_SVsToolboxActiveXDataProvider|35222106-bb44-11d0-8c46-00c04fc2aae2|

## <a name="see-also"></a>另請參閱

- [Managed 程式碼中的 COM 常數](../extensibility/com-constants-in-managed-code.md)
- [IDE 常數](../extensibility/ide-constants.md)
- [用於擴充專案 s ystems 的 IDE 定義命令](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
