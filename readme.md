# ����
1. docker desktop�C���X�g�[��
2. �y�v���L�V���̏ꍇ�zdocker desktop�Ƀv���L�V�ݒ聕docker-compose.yml�y�сA���K�w��`.env`�ɂ��ݒ�
3. �y�v���L�V���̏ꍇ�z�x�[�X�ƂȂ�C���[�W��pull���Ă����i`docker pull centos:7`�j
4. docker-compose.yml�̐ݒ�l�m�F�Bports�̃��[�J�����͋󂢂Ă���|�[�g��ݒ�
5. Dockerfile�Ɠ��K�w�i�R���e�L�X�g�ݒ�K�w�j��home�f�B���N�g���Ɍ��F�؂ɕK�v�ȃt�@�C����ansible.cfg�t�@�C���z�u  

# �r���h�����s
1. docker-compose.yml�̂���K�w��cd���A`docker-compose up -d --build`�����s
2. �N����Avolume��ansible-user�ȉ��̎w��f�B���N�g���iansible�v���O�����z�u�K�w�j�ƁA  
   jenkins�ݒ�t�@�C���K�w���}�E���g�����悤�ɐݒ肵�Ă܂�

# ���܂�
## �ғ����R���e�i�Ƀ��O�C��������@��
1. �R�}���h�v�����v�g���J��
2. `docker exec -it test-ansible_server_1 bash`�R�}���h���s

��docker-compose�Őݒ肵��ssh�|�[�g�t�H���[�h�Őڑ����邱�Ƃ��ł��܂�  
��F`ssh -o "UserKnownHostsFile=/dev/null" -o "StrictHostKeyChecking=no" -p 10022 ansible-user@localhost`  
�idocker�͋N�����Ƀz�X�g�����t���b�V�������̂ŁA�`�F�b�N�����I�v�V�����t���Ă܂��j

## jenkins���O�C��URL��
http://localhost:8081/

�ijenkins����ansible���s�ł���ƕ֗��Ȃ̂œ˂�����ł܂��j

## ��~���Ă�蒼��������
�ȉ��R�}���h�ŃR���e�i���C���[�W�폜�i�{�����[���͊J�����ʕ��܂܂��̂Ōʂɍ폜�����j  
`docker-compose down --rmi all`

������N�����A�{�����[�����ȊO�̕ύX�̓��t���b�V������܂�
