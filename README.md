# ResNet50V2 Quantization on CIFAR-10
This project demonstrates Post-Training Quantization (PTQ) and Quantization-Aware Training (QAT) for ResNet50V2 on CIFAR-10, 
comparing FP32 and INT8 models in terms of accuracy, model size, latency, and throughput.

## Objective
+ Optimize ResNet50V2 from FP32 to INT8 with minimal accuracy degradation.
+ Benchmark model performance across different quantization approaches.

## Deliverables
1. FP32 baseline, PTQ model, and QAT model
2. TorchScript / ONNX model exports
3. Standardized benchmarking scripts with tables and plots

## Results Comparison
```
=== Summary (threads: bench=4, acc=1; samples=5000 ) ===
Model          Size(MB)       Top1    P50(ms)    P90(ms)
FP32 (Keras)          -      92.53          -          -
PTQ-dynamic       24.58      92.20      37.88      45.27
PTQ-int8          24.78      89.82      33.46      39.35
QAT-int8          24.82      91.02      31.95      37.93
```

## Conclusions
+ Quantization compresses ResNet50V2 to ~25 MB (~4× smaller).
+ Dynamic PTQ nearly preserves FP32 accuracy (92.2% vs 92.5%).
+ Static PTQ drops accuracy more (89.8%).
+ QAT recovers accuracy (91.0%) while giving the best latency (~32 ms).
+ QAT-int8 is the best trade-off between size, speed, and accuracy.
