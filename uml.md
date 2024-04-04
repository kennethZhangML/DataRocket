@startuml

class MainWindow {
    - guiElements: GUIElement[]
    + show(): void
}

class DataCleaner {
    - gpuManager: GPUManager
    - dataModel: DataModel
    + removeDuplicates(): void
    + handleMissingValues(): void
    + otherCleaningOperations(): void
}

class CSVReader {
    - gpuManager: GPUManager
    + readCSV(): DataModel
}

class CSVWriter {
    - gpuManager: GPUManager
    + writeCSV(data: DataModel): void
}

class DataModel {
    - dataFields: DataField[]
    - dataMethods: DataMethod[]
    + manipulateData(): void
    + addField(field: DataField): void
    + removeField(field: DataField): void
    + addMethod(method: DataMethod): void
    + removeMethod(method: DataMethod): void
}

class GPUManager {
    - gpuDevice: GPUDevice
    + initialize(): void
    + configure(): void
    + control(): void
}

class GPUCleaner {
    - gpuDevice: GPUDevice
    + removeDuplicatesGPU(data: DataModel): void
    + handleMissingValuesGPU(data: DataModel): void
}

class GPUParser {
    - gpuDevice: GPUDevice
    + parseDataGPU(data: DataModel): void
}

class ErrorHandling {
    + displayErrorMessage(message: string): void
}

class PerformanceProfiler {
    + profilePerformance(): void
}

class GPUDevice {
    - memory: Memory
    + allocateMemory(): void
    + launchKernel(): void
    + transferData(): void
}

class Memory {
    + size: int
    + type: MemoryType
}

class DataField {
    - name: string
    - type: string
    + getName(): string
    + setName(name: string): void
    + getType(): string
    + setType(type: string): void
}

class DataMethod {
    - name: string
    - returnType: string
    + getName(): string
    + setName(name: string): void
    + getReturnType(): string
    + setReturnType(type: string): void
}

class GUIElement {
    - id: string
    - position: Point
    - size: Size
    - isVisible: boolean
    + show(): void
    + hide(): void
    + setPosition(x: int, y: int): void
    + getSize(): Size
    + setSize(width: int, height: int): void
}

class Point {
    - x: int
    - y: int
    + getX(): int
    + setX(x: int): void
    + getY(): int
    + setY(y: int): void
}

class Size {
    - width: int
    - height: int
    + getWidth(): int
    + setWidth(width: int): void
    + getHeight(): int
    + setHeight(height: int): void
}

MainWindow "1" --> "*" GUIElement
DataCleaner "1" *-- "1" GPUManager
CSVReader "1" *-- "1" GPUManager
CSVWriter "1" *-- "1" GPUManager
GPUCleaner "1" *-- "1" GPUManager
GPUParser "1" *-- "1" GPUManager
GPUCleaner "1" *-- "1" GPUDevice
GPUParser "1" *-- "1" GPUDevice
GPUManager "1" *-- "1" GPUDevice
DataType "1" *-- "*" DataField
DataType "1" *-- "*" DataMethod
GUIElement "1" *-- "1" Point
GUIElement "1" *-- "1" Size

@enduml
