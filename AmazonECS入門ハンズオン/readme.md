# Amazon ECS ����n���Y�I������

- �n���Y�I�� URL�F
  [Amazon ECS ����n���Y�I��](https://catalog.us-east-1.prod.workshops.aws/workshops/7ffc4ed9-d4b3-44dc-bade-676162b427cd/ja-JP)

- ����쐬������
  ![����쐬������](https://static.us-east-1.prod.workshops.aws/public/6f2ab827-2883-4f3f-ae31-63d20ce94521/static/assets/image-20220522130555288.png)

## �w�K�̗���

1. AWSCloud9 �� docker �R���e�i���쐬����
2. ECR �ɃR���e�i�C���[�W��ۑ�����
3. ECS �ŕۑ������R���e�i�C���[�W���ғ�������

## 1. AWSCloud9 �� docker �R���e�i���쐬����

AWS Cloud9 �̓u���E�U��Ŏ��s�ł��� IDE�B  
Linux �T�[�o�[��ŉғ����Ă���Adocker ���W���ŃC���X�g�[������Ă��邽�߁A�R���e�i�C���[�W�̍쐬�������ɍs����B  
Dockerfile �Ƃ����R���e�C���[�W�̍쐬���߂��܂Ƃ߂��t�@�C�����쐬���A��������Ƀr���h���č쐬����B

- Dockerfile �̎w����e

> os : ubuntu  
> webserver : apache2  
> �����y�[�W : index.html(helloworld)  
> �|�[�g : 80  
> apache �̎��s shell : run_apache.sh

### docker �R�}���h

- docker �o�[�W�����̊m�F

```
docker version
```

- ���ݍ쐬����Ă���R���e�i�C���[�W�̊m�F

```
docker images
```

- �R���e�i�C���[�W�̍쐬

```
docker build -t <�^�O��> .
```

- ���s���̃R���e�i�m�F

```
docker ps
```

- �R���e�i���s

```
docker run -d -p 8080:80 --name <�R���e�i��> <�^�O��>
```

- �R���e�i�� shell ���s

```
docker exec -i -t <�R���e�i��> bash
```

## 2. ECR �ɃR���e�i�C���[�W��ۑ�����

ECR �� AWS Cloud9 �̊���ō쐬�����R���e�i�C���[�W��ۊǂł��郌�W�X�g���B  
�ۊǕ������邽�߁A���|�W�g�����쐬���A�I���������|�W�g�����ɕۊǂ���B  
�ۊǂ����R���e�i�ւ� URI �����������̂ŁA�g�p����ۂ͂��� URI �ɕR�Â��Ďg�p���邱�ƂɂȂ�B

## 3. ECS �ŕۑ������R���e�i�C���[�W���ғ�������

ECS �̓R���e�i�𓮍삳���邽�߂̃T�[�r�X�B  
�g�p�ɂ́A�܂��N���X�^�[�Ƃ����R���e�i�𓮍삳���邽�߂̊����w�肷��P�ʂ��쐬����B  
���̃N���X�^�[�łǂ� VPC ���ŃR���e�i�����s�����邩���w�肷��B

<br>

���ɁA�^�X�N��`���쐬����B  
����̓R���e�i�̓���ɂ��Ē�`������̂ŁA�g�p����R���e�i�̎w��AOS �� CPU�A�������Ȃǂ̎��s�����w��ł���B

<br>

�Ō�ɃT�[�r�X���쐬����B  
����̓N���X�^�[�ƃ^�X�N���w�肵�āA���s�����邽�߂̃T�[�r�X�ƂȂ�B  
���[�h�o�����T�[��ێ��^�X�N���̎w�肪�o���邽�߁A��Q�������Ɏ����őΉ��\�ƂȂ�B  
�T�[�r�X�Ƀp�u���b�N IP �����蓖�Ă��邽�߁A�O���l�b�g���[�N����R���e�i�ɃA�N�Z�X���邱�Ƃ��ł���B
