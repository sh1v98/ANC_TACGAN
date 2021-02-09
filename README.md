Implementation of TAC-GAN for flower dataset 


Implementation Steps

Training:
1.	Download the flower images from here and extract the 102flowers.tgz file and copy the extracted jpg folder to Data/datasets/flowers in the working directory.
2.	Download the captions from here. Extract the downloaded file, copy the text_c10 folder and paste it in Data/datasets/flowers in the working directory.
3.	To extract skip-thought features: python dataprep.py --data_dir=Data --dataset=flowers
4.	To train the GAN and generate model: python train.py --dataset="flowers" --model_name=TAC-GAN


Testing:
1.	Write text descriptions in a file each per line and save at Data/text.txt 
2.	To extract skip-thoughts for the given captions: python encode_text.py--caption_file=Data/text.txt --data_dir=Data
3.	To generate images for the input captions: python generate_images.py --data_set=flowers --checkpoints_dir=Data/training/TAC_GAN/checkpoints --images_per_caption=30 --data_dir=Data

Evaluation:
We have used two metrics for evaluating TAC-GAN
1.	Inception-Scope
2.	MS-SSIM score

Inception score:
To calculate the inception score, use the following script,
	python inception_score.py --n_images=30000 --image_size=128
where 	n_images=	number of images to consider for calculating inception score.
	image_size=	size of the image to consider for calculating inception score.

MS-SSIM score:
To calculate the MS-SSIM score, use the following script,
python inception_score.py --output_dir=Data --data_dir=Data --dataset=flowers --syn_dataset_dir=Data/synthetic_datset/ds


