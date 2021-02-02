# modified-dcgan_tf
modify the code from https://github.com/carpedm20/DCGAN-tensorflow




I use tensorflow-2.3 in MACOS or tensorflow-2.5 in ubuntu16.04 cuda11.

So first,i use tf_upgrade_v2 change the old code with tf-v1.





Other changes can be found by APP filemerges.

For example,the function crop is ok in my files and you can change the number of test by parameter"generate_test_images".





about data:

you can dounload dataset "celebA" on http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html ,which names img_align_celeba.zip,remember to rename file name to celeba.

dataset "mnist" on http://yann.lecun.com/exdb/mnist/ ,including four files, train-images-idx3-ubyte.gz,train-labels-idx1-ubyte.gz,t10k-images-idx3-ubyte.gz,t10k-labels-idx1-ubyte.gz.

then you need to create a folder like this 

data
--celeba
--mnist
----train-images-idx3-ubyte
----train-labels-idx1-ubyte
----t10k-images-idx3-ubyte
----t10k-labels-idx1-ubyte


remember to create a folder named "out"






train:
python main.py --dataset mnist --input_height=28 --output_height=28 --train
python main.py --dataset celebA --input_height=108 --train --crop


(on ubuntu i use)
nohup python main.py --dataset mnist --input_height=28 --output_height=28 --train &
CUDA_VISIBLE_DEVICES=1 nohup python main.py --dataset celebA --input_height=108 --train --crop > myout.file 2>&1 &




test:
python main.py --dataset mnist --input_height=28 --output_height=28 --out_name=20210202.105019-data-mnist-x28.z100.uniform_signed.y28.b64 --visualize --generate_test_images=80

python main.py --dataset celebA --input_height=108 --crop --out_name=20210202.105019-data-celebA-x108.z100.uniform_signed.y64.b64 --visualize --generate_test_images=20











