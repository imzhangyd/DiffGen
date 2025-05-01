## DiffGen

### Environment
torch1.7.1
cuda10.2

```bash
conda env create -f ./env/env.yaml
```

### Raw Data Format
```
microtubule_low
    train
        Trainset_MICROTUBULE_snr_1_density_low.txt
        Trainset_MICROTUBULE_snr_2_density_low.txt
        Trainset_MICROTUBULE_snr_4_density_low.txt
    val
        Trainset_MICROTUBULE_snr_7_density_low.txt
    test
        Testset_MICROTUBULE_snr_1_density_low.txt
        Testset_MICROTUBULE_snr_2_density_low.txt
        Testset_MICROTUBULE_snr_4_density_low.txt
        Testset_MICROTUBULE_snr_7_density_low.txt       
microtubule_mid
    ... ...
vesicle_low
    ... ...
vesicle_mid
    ... ...
```

Each txt file content:
```
frame，trackid，x, y
... ...
```

### Data Preparation

```bash
python process_data.py
```

### Training

```bash
python main.py --config configs/microtubule_low_future1_sample1.yaml --dataset microtubule_low
python main.py --config configs/microtubule_mid_future1_sample1.yaml --dataset microtubule_mid

python main.py --config configs/vesicle_low_future1_sample1.yaml --dataset vesicle_low
python main.py --config configs/vesicle_mid_future1_sample1.yaml --dataset vesicle_mid
```

### Generation

```bash
python trajectory_gen_base_multiframe.py
```

### Evaluation

Prediction evaluation:
```bash
python eval_predict_diff_step.py
```

Generation evaluation:
```bash
python cal_feat_similarity_base_multiframe.py
```


