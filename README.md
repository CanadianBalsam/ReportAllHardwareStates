# ReportAllHardwareStates
i = 0
table = ZenTable()
table.Name = 'Hardware States'
table.Columns.Add('Hardware')
table.Columns.Add('State')
Zen.Application.Documents.Add(table)

hardwareSetting= Zen.Devices.ReadHardwareSetting()
componentIds = hardwareSetting.GetAllComponentIds()

for componentId in componentIds:
    parameterNames = hardwareSetting.GetAllParameterNames(componentId)
    for parameterName in parameterNames:
        parameterValue = str(hardwareSetting.GetParameter(componentId, parameterName))
        table.SetValue(i,0,parameterName)
        table.SetValue(i,1,parameterValue)
        i += 1
