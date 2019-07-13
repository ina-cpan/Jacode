# NAME

jacode.pl - Perl program for Japanese character code conversion

# �v��

## �g�p���@

```
require 'jacode.pl';
```

�p�b�P�[�W���� jacode �ł� jcode �ł��ǂ���ł����p�ł��܂��B

```
jacode::convert(\$line, $OUTPUT_encoding [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
jacode::xxx2yyy(\$line [, $option])
jacode::to($OUTPUT_encoding, $line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
jacode::jis($line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
jacode::euc($line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
jacode::sjis($line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
jacode::utf8($line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
jacode::jis_inout($JIS_Kanji_IN, $ASCII_IN)
jacode::get_inout($line)
jacode::cache()
jacode::nocache()
jacode::flushcache()
jacode::flush()
jacode::h2z_xxx(\$line)
jacode::z2h_xxx(\$line)
jacode::getcode(\$line)
jacode::getcode2(\$line [, $encoding_suggestion])
jacode::tr(\$line, $from, $to [, $option])
jacode::trans($line, $from, $to [, $option])
jacode::init()
$jacode::convf{'xxx', 'yyy'}
$jacode::z2hf{'xxx'}
$jacode::h2zf{'xxx'}
```

# �T�v

���� "jacode.pl" �͕����������̕ϊ����s�����߂̃\�t�g�E�F�A�ł��B�̑�a������
�̍쐬���ꂽ "jcode.pl" ����� "pkf" �����Ƃɂ��č���Ă���A�����̃\�t�g
�E�F�A����X���[�Y�Ɉڍs�ł���悤�l������Ă��܂��B

Perl ���C�u�����Ƃ��ė��p����� "jcode.pl" �̂悤�ɁA�R�}���h���C���v���O����
�Ƃ��ė��p����� "pkf" �̂悤�ɋ@�\���܂��B�R�}���h���C���I�v�V�����̐�����
�����I�v�V�����������Ɏ��s���邱�ƂŎQ�Ƃł��܂��B

���� jacode.pl �P�̂� JIS�A�V�t�gJIS�AEUC-JP�AUTF-8 ���������Ƃ��ł��AEncode
���W���[�������p�ł�����ł���� jacode.pl �� Encode ���W���[�����Ăяo����
�Ƃɂ��A���܂��܂ȕ����������̕ϊ����s�����Ƃ��ł��܂��B

�Ȃ��A���̏ꍇ�ł� jcode.pl �̃C���^�t�F�[�X���g�����Ƃ��ł���̂ŁA���Ȃ��J��
�� jacode.pl �ɓ����E�ڍs���邱�Ƃ��ł��܂��B

## ��ȓ���

* jcode.pl ��ʌ݊��̋@�\�E�v���O���~���O�C���^�t�F�[�X
* pkf �R�}���h��ʌ݊��̋@�\�E�g�p���@
* Perl4 �X�N���v�g�ł�����APerl5 �X�N���v�g�ł�����
* Encode::from_to �̃��b�p�[�Ƃ��ċ@�\����
* �����ɓn���ė��p�\�ȃ\�t�g�E�F�A
* ���p�J�^�J�i���T�|�[�g
* UTF-8 ���� cp932 �ւ̕ϊ��͈ȉ��̃e�[�u���𗘗p����

  http://unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WINDOWS/CP932.TXT
  http://support.microsoft.com/kb/170559/ja
  (JIS X 0221:2007 BASIC JAPANESE and COMMON JAPANESE)

* ���̃\�t�g�E�F�A�ɂ���� UTF8 �t���O�͉B�������
* �C���^�t�F�[�X���������@���I�u�W�F�N�g�w���𗘗p���Ă��Ȃ�
* �`���I�ȃv���O���~���O�Z�@�𗘗p�������邱�Ƃ��ł���

# ������@

����2018�N2���̎��_�ł́A�ȉ��� URL �� jacode.pl ������܂��B

  http://search.cpan.org/dist/jacode/

�t�@�C�� "jacode.pl" �𒼐ڃ_�E�����[�h�����ꍇ�́A�t�@�C���� POD �̏I
���ł���u=cut�v�ŏI����Ă��邱�Ƃ��m�F���Ă��������B�u=cut�v�ŏI���
�Ă��Ȃ��ꍇ�͂��̃t�@�C���͊��S�ł͂Ȃ��A����ɓ��삵�܂���B

# �C���X�g�[�����@

�t�@�C���̖��O�� "jacode.pl" �Ƃ��āAPerl �̓���ϐ�  @INC �Ɋ܂܂�邢
���ꂩ�̃t�H���_�Ɋi�[���܂��B�ǂ��ɒu���΂悢���������ꍇ�A�A�v���P�[
�V�����v���O�����Ɠ����t�H���_�ɔz�u����Ƃ悢�ł��傤�B

# �ˑ����Ă���\�t�g�E�F�A

���̃\�t�g�E�F�A�� perl 4.036 �������͂���ȍ~�� perl �Ŏ��s�ł��܂��B

# �T�u���[�`���̌Ăяo�����@

jacode.pl ���̃T�u���[�`���� jacode �p�b�P�[�W�Ɋ܂܂�Ă��܂��B�܂�
jcode.pl �Ƃ̌݊������m�ۂ���ړI�� jcode �p�b�P�[�W�ɂ��܂܂�Ă���A
�ǂ���̃p�b�P�[�W���ł����p�ł���悤�ɂȂ��Ă��܂��B�ȉ��̐����ł�
�p�b�P�[�W���� jacode �Ƃ��Ă��܂��B

# �g�p���Ă��� perl �C���^�v���^�� Perl5 �̏ꍇ

�T�u���[�`�����̑O�� jacode:: ��t�����܂��B�Ⴆ�� convert() �̏ꍇ��

jacode::convert(...);

�̂悤�ɂ��ČĂяo���܂��B

# jcode.pl �Ƃ̌݊������l������K�v������ꍇ

jcode.pl �𗘗p���č쐬���ꂽ�v���O������ێ炷��A�Ȃǂ̖ړI�� jcode.pl
�̃C���^�t�F�[�X�𗘗p�������ꍇ�A�ȉ��̂悤�� jcode �p�b�P�[�W�ŃT�u���[
�`���𗘗p���邱�Ƃ��ł��܂��B

&jcode'convert(...);

# �T�u���[�`��

## jacode::convert

�C�ӂ̕����������ɕϊ�����

### ����

```
jacode::convert(\$line, $OUTPUT_encoding [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
```

### ���� \\$line

�ϊ���������������X�J���[�ϐ� $line �Ɋi�[���A���̃��t�@�����X�������ɂ��܂��B
�z��̗v�f�̃��t�@�����X��n�b�V���̗v�f�̃��t�@�����X���w�肷�邱�Ƃ��ł���
���B���̃��t�@�����X�ɂ��C���^�t�F�[�X�͓����I�ɖ��p�ȃR�s�[�����Ȃ�����
��ړI�Ƃ��Ă��܂��B�T�u���[�`�����s��A$line �̓��e�͏��������܂��B

### ���� $OUTPUT_encoding

�ϊ���̕������������w�肵�܂��B
���̃\�t�g�E�F�A�P�̂ŕϊ��ł��镄���������͈ȉ��̂Ƃ���ł��B

* 'jis' JIS�R�[�h
* 'sjis' �V�t�gJIS�R�[�h
* 'euc' EUC-JP �R�[�h
* 'utf8' UTF-8 �R�[�h
* 'noconv' �ϊ����s�������Ȃ��ꍇ

��L�ȊO�̕������������w�肵���ꍇ�́AEncode ���W���[�������p�ł�����ł���
�� Encode::from_to() ���Ăяo����܂��B

### ���� $INPUT_encoding

�ϊ��O�̕������������w�肵�܂��B���̈����� jcode.pl �ƌ݊�����ۂ��߂ɏȗ���
�\�ƂȂ��Ă��܂����A���܂�ȗ�����ׂ��ł͂���܂���B�ȗ����ɂ�
jacode::getcode() �������ŌĂяo����A�ϊ��O�̕�������������������܂��B���̐�
���͊ԈႦ��ꍇ������܂��B

���̃\�t�g�E�F�A�P�̂ŕϊ��ł��镄���������͈ȉ��̂Ƃ���ł��B

* 'jis' JIS�R�[�h
* 'sjis' �V�t�gJIS�R�[�h
* 'euc' EUC-JP �R�[�h
* 'utf8' UTF-8 �R�[�h

��L�ȊO�̕������������w�肵���ꍇ�́AEncode ���W���[�������p�ł�����ł���
�� Encode::from_to() ���Ăяo����܂��B

### ���� $option

���p�J�^�J�i�̕ϊ����̃I�v�V�������w�肵�܂��B���̈����͏ȗ��\�ł��B

* 'z' $line �Ɋ܂܂�锼�p�J�^�J�i��S�p�J�^�J�i�ɕϊ����܂�(zenkaku)�B
* 'h' $line �Ɋ܂܂��S�p�J�^�J�i�𔼊p�J�^�J�i�ɕϊ����܂�(hankaku)�B

### �@�\

��������w�肵�������������ɕϊ�����

���̊֐��� $line �Ɋi�[����Ă��镶����� $OUTPUT_encoding �Ŏw�肵������������
�ɕϊ����܂��B

### �߂�l(�X�J���[�R���e�L�X�g�̏ꍇ)

$line �̕ϊ���̕�����������Ԃ��܂��B

### �߂�l(���X�g�R���e�L�X�g�̏ꍇ)

* ��1�v�f �ϊ��T�u���[�`���ւ̃��t�@�����X
* ��2�v�f $line �̕ϊ���̕���������

### �⑫����

���̃T�u���[�`�����쐬���ꂽ�����A�������͔��ɋM�d���������߁A�ϊ��O�̃���
���ƕϊ���̃������͓���̗̈�𗘗p���Ă��܂��B�ϊ��������I���ƕϊ��O�̕�
����͂Ȃ��Ȃ�܂��B�܂��ϊ��O�̕����������͎���������s����悤�ɂȂ��Ă���
���߁A�ȗ��\�Ȃ悤�ɍ쐬����Ă���A���̂��߈����̏������A

$OUTPUT_encoding �̎��� $INPUT_encoding

�ƂȂ��Ă��܂��B

## jacode::xxx2yyy

���������� xxx ���� ���������� yyy �ɕϊ�����

### ����

xxx ����� yyy �ɂ� jis, euc, sjis, utf8 �̂��������ꂩ������A�S���ňȉ��� 16
�̃T�u���[�`��������܂��B

```
jacode::euc2euc(\$line [, $option])
jacode::euc2jis(\$line [, $option])
jacode::euc2sjis(\$line [, $option])
jacode::jis2jis(\$line [, $option])
jacode::jis2euc(\$line [, $option])
jacode::jis2sjis(\$line [, $option])
jacode::sjis2sjis(\$line [, $option])
jacode::sjis2euc(\$line [, $option])
jacode::sjis2jis(\$line [, $option])
jacode::utf82utf8(\$line [, $option])
jacode::utf82jis(\$line [, $option])
jacode::utf82euc(\$line [, $option])
jacode::utf82sjis(\$line [, $option])
jacode::jis2utf8(\$line [, $option])
jacode::euc2utf8(\$line [, $option])
jacode::sjis2utf8(\$line [, $option])
```

### ���� \\$line

�ϊ���������������X�J���[�ϐ� $line �Ɋi�[���A���̃��t�@�����X�������ɂ��܂��B
�z��̗v�f�̃��t�@�����X��n�b�V���̗v�f�̃��t�@�����X���w�肷�邱�Ƃ��ł��܂��B
�T�u���[�`�����s��A$line �̓��e�͏��������܂��B

### ���� $option

���p�J�^�J�i�̕ϊ����̃I�v�V�������w�肵�܂��B���̈����͏ȗ��\�ł��B

* 'z' $line �Ɋ܂܂�锼�p�J�^�J�i��S�p�J�^�J�i�ɕϊ����܂�(zenkaku)�B
* 'h' $line �Ɋ܂܂��S�p�J�^�J�i�𔼊p�J�^�J�i�ɕϊ����܂�(hankaku)�B

### �@�\

$line �Ɋi�[����Ă���A���������� xxx �̕�����𕄍������� yyy �ɕϊ����܂��B
���̃T�u���[�`���̌Ăяo���ɂ���ĕϐ� $line �̓��e�����������܂��B

### �߂�l

�ߋ��̎����ɂ����ẮA�ϊ��ɐ������������悻�̕�������Ԃ��A�Ƃ��Ă������Ƃ���
��܂����B���̏ꍇ�A�����ϊ��ł��Ȃ��ꍇ�� 0 ���Ԃ�܂��B�Ȃ��A�����ɂ���Ă�
�������ł͂Ȃ��o�C�g����Ԃ��A�ƋL�q����Ă��܂��B

## jacode::to

�����������ϊ���̕������Ԃ�

### ����

```
jacode::to($OUTPUT_encoding, $line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
```

### ���� $OUTPUT_encoding

�ϊ���̕������������w�肵�܂��B

### ���� $line

�ϊ���������������X�J���[�ϐ� $line �Ɋi�[���܂��B

### ���� $INPUT_encoding

�ϊ��O�̕������������w�肵�܂��B���̈����� jcode.pl �ƌ݊�����ۂ��߂ɏȗ���
�\�ƂȂ��Ă��܂����A���܂�ȗ�����ׂ��ł͂���܂���B�ȗ����ɂ�
jacode::getcode() �������ŌĂяo����A�ϊ��O�̕�������������������܂��B���̐�
���͊ԈႦ��ꍇ������܂��B

���̃\�t�g�E�F�A�P�̂ŕϊ��ł��镄���������͈ȉ��̂Ƃ���ł��B

* 'jis' JIS�R�[�h
* 'sjis' �V�t�gJIS�R�[�h
* 'euc' EUC-JP �R�[�h
* 'utf8' UTF-8 �R�[�h

��L�ȊO�̕������������w�肵���ꍇ�́AEncode ���W���[�������p�ł�����ł���
�� Encode::from_to() ���Ăяo����܂��B

### ���� $option

���p�J�^�J�i�̕ϊ����̃I�v�V�������w�肵�܂��B���̈����͏ȗ��\�ł��B

* 'z' $line �Ɋ܂܂�锼�p�J�^�J�i��S�p�J�^�J�i�ɕϊ����܂�(zenkaku)�B
* 'h' $line �Ɋ܂܂��S�p�J�^�J�i�𔼊p�J�^�J�i�ɕϊ����܂�(hankaku)�B

### �@�\

$line �Ŏw�肵��������� $OUTPUT_encoding �Ŏw�肵�������������ɕϊ����ĕԂ���
���B

�T�u���[�`�����s��A$line �̓��e�͕ω����܂���B

### �߂�l

�����������ϊ���̕�����ł��B

### �⑫����

�����̊֐��́A call/return-by-value �C���^�[�t�F�[�X�Ƃ��ĊȒP�Ɏg���܂��B
�Ⴆ�� s///e ���Z�q���ŗp���邱�Ƃ��ł��܂��B

## jacode::xxx

������������ xxx �ɕϊ�����

### ����

xxx �ɂ� jis, euc, sjis, utf8 �̂��������ꂩ������܂��B

```
jacode::jis($line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
jacode::euc($line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
jacode::sjis($line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
jacode::utf8($line [, $INPUT_encoding [, $option [, $INPUT_encoding_suggestion]]])
```

### ���� $line

�ϊ���������������X�J���[�ϐ� $line �Ɋi�[���܂��B

### ���� $INPUT_encoding

�ϊ��O�̕������������w�肵�܂��B���̈����� jcode.pl �ƌ݊�����ۂ��߂ɏȗ���
�\�ƂȂ��Ă��܂����A���܂�ȗ�����ׂ��ł͂���܂���B�ȗ����ɂ�
jacode::getcode() �������ŌĂяo����A�ϊ��O�̕�������������������܂��B���̐�
���͊ԈႦ��ꍇ������܂��B

���̃\�t�g�E�F�A�P�̂ŕϊ��ł��镄���������͈ȉ��̂Ƃ���ł��B

* 'jis' JIS�R�[�h
* 'sjis' �V�t�gJIS�R�[�h
* 'euc' EUC-JP �R�[�h
* 'utf8' UTF-8 �R�[�h

��L�ȊO�̕������������w�肵���ꍇ�́AEncode ���W���[�������p�ł�����ł���
�� Encode::from_to() ���Ăяo����܂��B

### ���� $option

���p�J�^�J�i�̕ϊ����̃I�v�V�������w�肵�܂��B���̈����͏ȗ��\�ł��B

* 'z' $line �Ɋ܂܂�锼�p�J�^�J�i��S�p�J�^�J�i�ɕϊ����܂�(zenkaku)�B
* 'h' $line �Ɋ܂܂��S�p�J�^�J�i�𔼊p�J�^�J�i�ɕϊ����܂�(hankaku)�B

### �@�\

$line �Ŏw�肵����������A���������� $INPUT_encoding ����T�u���[�`�����Ŏw��
����镄���������ɕϊ����A���̕������Ԃ��܂��B

�T�u���[�`�����s��A$line �̓��e�͕ω����܂���B

### �߂�l

�ϊ���̕������Ԃ��܂��B

## jacode::jis_inout

### ����

```
jacode::jis_inout($JIS_Kanji_IN, $ASCII_IN)
```

�G�X�P�[�v�V�[�P���X�̕ύX

### ���� $JIS_Kanji_IN

2�o�C�g�����ւ̃G�X�P�[�v�V�[�P���X���w�肵�܂��B

### ���� $ASCII_IN

1�o�C�g�����ւ̃G�X�P�[�v�V�[�P���X���w�肵�܂��B

### �@�\

jacode::jis_inout() �́AJIS �R�[�h�ŗp����G�X�P�[�v�V�[�P���X��ύX���A�ύX
��̒l��Ԃ��܂��B$JIS_Kanji_IN �ɂ́A2�o�C�g�����ւ̃G�X�P�[�v�V�[�P���X���A
$ASCII_IN �ɂ́A�P�o�C�g�����ւ̃G�X�P�[�v�V�[�P���X���w�肵�܂��Bjacode.pl ��
�f�t�H���g�ł́A$JIS_Kanji_IN �ɂ� JIS X 0208-1983(�VJIS83)�̊J�n������
"1Bh 24h 42h" �� 3 �o�C�g���A$ASCII_IN �ɂ� ASCII �����̊J�n������
"1Bh 28h 42h" �� 3 �o�C�g�����ꂼ��w�����ꂽ��ԂƂȂ��Ă��܂��B
jacode::jis_inout() �͕K�v�ɉ����Ă�����ύX�ł��܂��B

�Ȃ��A�����͏ȗ��`�� 1 �o�C�g�Ŏw�肷�邱�Ƃ��ł��܂��B

* ESC-$-@ JIS C 6226-1978 �̏ꍇ(�ȗ��`�́u@�v)
* ESC-$-B JIS X 0208-1983 �̏ꍇ(�ȗ��`�́uB�v)
* ESC-&-@-ESC-$-B JIS X 0208-1990 �̏ꍇ(�ȗ��`�́u&�v)
* ESC-$-(-O JIS X 0213:2000 ���ʂ̏ꍇ(�ȗ��`�́uO(�I�[)�v)
* ESC-$-(-Q JIS X 0213:2004 ���ʂ̏ꍇ(�ȗ��`�́uQ�v)

### �߂�l

�ύX��̃G�X�P�[�v�V�[�P���X�̃��X�g ($JIS_Kanji_IN, $ASCII_IN) ��Ԃ��܂��B

## jacode::get_inout

JIS �����������񂩂�A�G�X�P�[�v�V�[�P���X���擾����

### ����

```
jacode::get_inout($line)
```

### ���� $line

�G�X�P�[�v�V�[�P���X�𒲂ׂ�����������X�J���[�ϐ� $line �Ɋi�[���܂��B

### �@�\

$line ����A���� jacode::jis_inout() �ɂ���Đݒ肳��Ă���G�X�P�[�v�V�[�P��
�X�̃o�C�g���T���āA������΂��̃G�X�P�[�v�V�[�P���X��Ԃ��A������Ȃ���
�� undef ��Ԃ��܂��B

### �߂�l

jacode::jis_inout() �Ɠ��l�ɁA($JIS_Kanji_IN, $ASCII_IN) �̌`���ł��B 

* ESC-$-@ JIS C 6226-1978 �̏ꍇ
* ESC-$-B JIS X 0208-1983 �̏ꍇ
* ESC-&-@-ESC-$-B JIS X 0208-1990 �̏ꍇ
* ESC-$-(-O JIS X 0213:2000 ���ʂ̏ꍇ
* ESC-$-(-Q JIS X 0213:2004 ���ʂ̏ꍇ

## jacode::h2z_xxx

���p�J�^�J�i��S�p�J�^�J�i�ɕϊ�

### ����

xxx �ɂ� jis, euc, sjis, utf8 �̂��������ꂩ������܂��B

```
jacode::h2z_jis(\$line)
jacode::h2z_euc(\$line)
jacode::h2z_sjis(\$line)
jacode::h2z_utf8(\$line)
```

### ���� \\$line

�ϊ���������������X�J���[�ϐ� $line �Ɋi�[���A���̃��t�@�����X�������ɂ��܂��B
�z��̗v�f�̃��t�@�����X��n�b�V���̗v�f�̃��t�@�����X���w�肷�邱�Ƃ��ł��܂��B
�T�u���[�`�����s��A$line �̓��e�͏��������܂��B

### �@�\

$line �Ŏw�肵��������Ɋ܂܂�锼�p�J�^�J�i��S�p�J�^�J�i�ɕϊ����܂��B
xxx �ɂ͕����������Ƃ��� jis, euc, sjis, utf8 �̂����ꂩ������܂��B
���̃T�u���[�`�����s��A$line �̓��e�������ς��܂��B

### �߂�l

�ߋ��̎����ɂ����ẮA�ϊ��ɐ������������悻�̕�������Ԃ��A�Ƃ��Ă������Ƃ���
��܂����B���̏ꍇ�A�����ϊ��ł��Ȃ��ꍇ�� 0 ���Ԃ�܂��B

## jacode::z2h_xxx

�S�p�J�^�J�i�𔼊p�J�^�J�i�ɕϊ�

### ����

xxx �ɂ� jis, euc, sjis, utf8 �̂��������ꂩ������܂��B

```
jacode::z2h_jis(\$line)
jacode::z2h_euc(\$line)
jacode::z2h_sjis(\$line)
jacode::z2h_utf8(\$line)
```

### ���� \\$line

�ϊ���������������X�J���[�ϐ� $line �Ɋi�[���A���̃��t�@�����X�������ɂ��܂��B
�z��̗v�f�̃��t�@�����X��n�b�V���̗v�f�̃��t�@�����X���w�肷�邱�Ƃ��ł��܂��B
�T�u���[�`�����s��A$line �̓��e�͏��������܂��B

### �@�\

$line �Ŏw�肵��������Ɋ܂܂��S�p�J�^�J�i�𔼊p�J�^�J�i�ɕϊ����܂��B
xxx �ɂ͕����������Ƃ��� jis, euc, sjis, utf8 �̂����ꂩ������܂��B
���̃T�u���[�`�����s��A$line �̓��e�������ς��܂��B

### �߂�l

�ߋ��̎����ɂ����ẮA�ϊ��ɐ������������悻�̕�������Ԃ��A�Ƃ��Ă������Ƃ���
��܂����B���̏ꍇ�A�����ϊ��ł��Ȃ��ꍇ�� 0 ���Ԃ�܂��B

## jacode::getcode

������̕����������𐄑����ĕԂ�

### ����

```
jacode::getcode(\$line)
```

�����������𒲂ׂ�

### ���� \\$line

�����������𒲂ׂ�����������X�J���[�ϐ� $line �Ɋi�[���A���̃��t�@�����X������
�ɂ��܂��B�z��̗v�f�̃��t�@�����X��n�b�V���̗v�f�̃��t�@�����X���w�肷�邱��
���ł��܂��B

### �@�\

���̃T�u���[�`���́A$line �ŗ^����ꂽ������̕����������𐄑����ĕԂ��܂��B

### �߂�l(�X�J���[�R���e�L�X�g�̏ꍇ)

�ȉ��̂����ЂƂ��Ԃ�܂��B

* 'jis' $line �� JIS �Ɛ��������
* 'sjis' $line �� �V�t�gJIS �Ɛ��������
* 'euc' $line �� EUC-JP �Ɛ��������
* 'utf8' $line �� UTF-8 �Ɛ��������
* 'binary' $line �͔񕶎����܂�
* undef ��L�̂�����ł��Ȃ�

### �߂�l(���X�g�R���e�L�X�g�̏ꍇ)

�ȉ���2�̒l���߂�l�ɂȂ�܂��B

* ��1�̗v�f

�����Ƃ��ė^����ꂽ�����񒆁A���̃T�u���[�`�������f���������������ɊY������
�o�C�g��(�u�������v�Ə����ꂽ���������݂��邪�A�o�C�g����������)

* ��2�̗v�f

���̃T�u���[�`�������f��������������

### ��

```
#        .........1...
#        1234567890123 ���o�C�g��
$line = '����ABC������';           # $line �� EUC-JP �R�[�h�Ƃ���B
$code = jacode::getcode(\$line);   # $code �ɂ́A"euc" ��������B
@code = jacode::getcode(\$line);   # @code �ɂ́A(13, "euc") ��������B
```

���̃T�u���[�`���͔��p�J�^�J�i�A����т���ɑ������镄�����o�������ꍇ�ł����
�������Ƃ͂Ȃ��A����̑ΏۂƂ��܂��B

jacode.pl �� jcode.pl �Ƃ͈قȂ�AUTF-8 ���T�|�[�g���Ă��邽�߂�
jacode::getcode() �̖߂�l�̐��m���͒Ⴍ�Ȃ��Ă��܂��B
���̂��߁A���̃T�u���[�`���̗��p�͂��͂␄������Ă��܂���B

## jacode::getcode2

������̕����������𐄑����ĕԂ�

### ����

```
jacode::getcode2(\$line [, $encoding_suggestion])
```

�����������𒲂ׂ�

### ���� \\$line

�����������𒲂ׂ�����������X�J���[�ϐ� $line �Ɋi�[���A���̃��t�@�����X������
�ɂ��܂��B�z��̗v�f�̃��t�@�����X��n�b�V���̗v�f�̃��t�@�����X���w�肷�邱��
���ł��܂��B

### �@�\

���̃T�u���[�`���́A$line �ŗ^����ꂽ������̕����������𐄑����ĕԂ��܂��B

### �߂�l(�X�J���[�R���e�L�X�g�̏ꍇ)

�ȉ��̂����ЂƂ��Ԃ�܂��B

* 'jis' $line �� JIS �Ɛ��������
* 'sjis' $line �� �V�t�gJIS �Ɛ��������
* 'euc' $line �� EUC-JP �Ɛ��������
* 'utf8' $line �� UTF-8 �Ɛ��������
* 'binary' $line �͔񕶎����܂�
* undef ��L�̂�����ł��Ȃ�

### �߂�l(���X�g�R���e�L�X�g�̏ꍇ)

�ȉ���2�̒l���߂�l�ɂȂ�܂��B

* ��1�̗v�f

�����Ƃ��ė^����ꂽ�����񒆁A���̃T�u���[�`�������f���������������ɊY������
�o�C�g��(�u�������v�Ə����ꂽ���������݂��邪�A�o�C�g����������)

* ��2�̗v�f

���̃T�u���[�`�������f��������������

### ��

```
#        .........1...
#        1234567890123 ���o�C�g��
$line = '����ABC������';           # $line �� EUC-JP �R�[�h�Ƃ���B
$code = jacode::getcode2(\$line);   # $code �ɂ́A"euc" ��������B
@code = jacode::getcode2(\$line);   # @code �ɂ́A(13, "euc") ��������B
```

���̃T�u���[�`���͔��p�J�^�J�i�A����т���ɑ������镄�����o�������ꍇ�ł����
�������Ƃ͂Ȃ��A����̑ΏۂƂ��܂��B

jacode.pl �� jcode.pl �Ƃ͈قȂ�AUTF-8 ���T�|�[�g���Ă��邽�߂�
jacode::getcode2() �̖߂�l�̐��m���͒Ⴍ�Ȃ��Ă��܂��B
���̂��߁A���̃T�u���[�`���̗��p�͂��͂␄������Ă��܂���B

## jacode::cache

�L���b�V�����J�n

### ����

```
jacode::cache()
```

### ����

����܂���B

### �@�\

jacode.pl �́A���Z�ɂ���ĕ����������̕ϊ����s���ꍇ������܂��B��x�v�Z����
���ʂ̓n�b�V���ɕۑ�����A�����������o�������ꍇ�ɍė��p����܂��B�ʏ�͂���
�@�\�� ON �ɂȂ��Ă���̂ŁAON/OFF ��؂�ւ��Ȃ��̂ł���Έӎ�����K�v�͂�
��܂���B

### �߂�l

jacode::cache() ���Ăяo�����O�̃L���b�V���� ON/OFF �̏�Ԃ�Ԃ��܂��B

## jacode::nocache

�L���b�V���̒�~

### ����

```
jacode::nocache()
```

### ����

����܂���B

### �@�\

jacode.pl ���p����L���b�V�����~���܂��B

### �߂�l

jacode::nocache() ���Ăяo�����O�̃L���b�V���� ON/OFF �̏�Ԃ�Ԃ��܂��B

## jacode::flushcache

�L���b�V���̏���

### ����

```
jacode::flushcache()
```

### ����

����܂���B

### �@�\

jacode.pl �̃L���b�V���ɕۑ�����Ă�����e���������܂��B

### �߂�l

����܂���B

## jacode::flush

�L���b�V���̏���

### ����

```
jacode::flush()
```

### ����

����܂���B

### �@�\

�����ŃT�u���[�`�� jacode::flushcache() ���Ăяo���܂��B���̃T�u���[�`���͌�
���h�L�������g�̌����~���ړI�ő��݂��Ă��܂��B

### �߂�l

����܂���B

## jacode::tr

perl �� tr/// ���Z�q�̋@�\��͕�

### ����

```
jacode::tr(\$line, $from, $to [,$option])
```

### ���� \\$line

�ϊ���������������X�J���[�ϐ� $line �Ɋi�[���A���̃��t�@�����X�������ɂ��܂��B
�z��̗v�f�̃��t�@�����X��n�b�V���̗v�f�̃��t�@�����X���w�肷�邱�Ƃ��ł��܂��B
�T�u���[�`�����s��A$line �̓��e�͏��������܂��B

### ���� $from

�ϊ��������ϊ��O�̕�������ׂċL�q���܂��B

### ���� $to

���� $from �̏��ɕϊ��������ϊ���̕�������ׂċL�q���܂��B

### ���� $option

'd' ���w�肵���ꍇ�� tr///d �̋@�\��͕킵�܂��B

### �@�\

���̃T�u���[�`���� Perl �� tr/// ���Z�q�̋@�\��͕킵�܂��B
jcode.pl ����� jacode.pl �͕����������̕ϊ���ړI�Ƃ������C�u�����Ȃ̂�
tr/// �̖͕�͋@�\�I�ɏ\���ł͂���܂���B

$line �̕����񒆂� $from �Ɋ܂܂�Ă��镶��������΁A$to �̑Ή����镶���ɒu��
�����܂��B$line, $from, $to �̕����������͈�v������K�v������AJIS �܂���
EUC-JP �݂̂����p�ł��܂��B�Ȃ��AJIS X 0212(�ʏ́A�⏕����)�͈������Ƃ��ł���
����B

�����V�t�g JIS ���邢�� UTF-8 �̏ꍇ�́Ajacode::convert() �ɂ���ĕ�����������
EUC-JP �܂��� JIS �ɕϊ����A���̌� jacode::tr() �̎��s���s���A����ɂ��̌�
jacode::convert() �ɂ���Č��̕����������ɖ߂��K�v������܂��B

$from�A����� $to �ɂ� "a-z" �̂悤�ɔ͈͂��w�肷�邱�Ƃ��ł��܂��B���̋L�@��
���K�\���̕����N���X�Ɏ��Ă��܂��� "[a-z]" �̂悤�Ɋp�������ň͂ޕK�v�͂����
����B"[", "]" �ň͂ނƂ����̕������ϊ��ΏۂƂ��Ĉ����܂��B

2�o�C�g�����ɂ��͈͎w��̏ꍇ�A�J�n�����ƏI�������̂��ꂼ��̑�1�o�C�g�̒l
�͓����ł���K�v������܂��B

$option �ɂ� 'd' ���w�肷�邱�Ƃ��ł��܂��B'd' ���w�肵���ꍇ�́A$from �Ɋ܂�
��Ă��� $to �Ɋ܂܂�Ă��Ȃ������� $line �ɏo�������ꍇ�A�ϊ���̕����񂩂�
��菜����܂��B����� tr///d �̋@�\��͕킷�邱�Ƃ��Ӑ}���Ă��܂��B

�n�C�t���u - �v���g��u������ꍇ�A�n�C�t����͈͎w��̍Ō�ɔz�u���܂��B

```
$line = '�s�d�k�O�R�|�X�X�X�X�|�X�X�X�X';              # �S�p����
jacode::tr(\$line, '�O-�X�`-�y��-���|', '0-9A-Za-z-'); # ���p�ɒu�������
print $line;                                           # "TEL03-9999-9999" �ƕ\��
```

### �߂�l

�ϊ����������̐���Ԃ��܂��B

## jacode::trans

tr/// ���Z�q�̋@�\��͕�

### ����

```
jacode::trans($line, $from, $to [,$option])
```

### ���� $line

�ϊ���������������X�J���[�ϐ� $line �Ɋi�[���A�����ɂ��܂��B�z��̗v�f�̃��t�@
�����X��n�b�V���̗v�f�̃��t�@�����X���w�肷�邱�Ƃ��ł��܂��B

### ���� $from

�ϊ��������ϊ��O�̕�������ׂċL�q���܂��B

### ���� $to

���� $from �̏��ɕϊ��������ϊ���̕�������ׂċL�q���܂��B

### ���� $option

'd' ���w�肵���ꍇ�� tr///d �̋@�\��͕킵�܂��B

### �@�\

jacode::tr() �Ɠ��l�� Perl �� tr/// �̋@�\��͕킵�܂��Bjacode::tr() �ƈقȂ�A
$line �͏����ς��܂���B

### �߂�l

�ϊ���̕������Ԃ��܂��B

## %jacode::convf

�����������ϊ��̃T�u���[�`�� jacode::xxx2yyy() �̃��t�@�����X���擾����

### ����

```
$jacode::convf{'xxx', 'yyy'}
```

### �@�\

xxx ����� yyy �� jis, euc, sjis, utf8 �̂����ꂩ���w�肷��� jacode::xxx2yyy()
�̃T�u���[�`���̃��t�@�����X���擾���邱�Ƃ��ł��܂��B

## %jacode::h2zf

�����������ϊ��̃T�u���[�`�� jacode::h2z_xxx() �̃��t�@�����X���擾����

### ����

```
$jacode::h2zf{'xxx'}
```

### �@�\

xxx �� jis, euc, sjis, utf8 �̂����ꂩ���w�肷��� jacode::h2z_xxx() �̃T�u���[
�`���̃��t�@�����X���擾���邱�Ƃ��ł��܂��B

## %jacode::z2hf

�����������ϊ��̃T�u���[�`�� jacode::z2h_xxx() �̃��t�@�����X���擾����

### ����

```
$jacode::z2hf{'xxx'}
```

### �@�\

xxx �� jis, euc, sjis, utf8 �̂����ꂩ���w�肷��� jacode::z2h_xxx() �̃T�u���[
�`���̃��t�@�����X���擾���邱�Ƃ��ł��܂��B

## jacode::init

�ϐ��̏��������s��

### ����

```
jacode::init()
```

### ����

����܂���B

### �@�\

jacode �p�b�P�[�W���̕ϐ������������܂��Bjacode.pl �� require 'jacode.pl';
�ɂ���ė��p����ꍇ�́A�����I�ɌĂяo����܂��Bjacode.pl �̓��e���A�v���P�[
�V�����v���O�����̒��ɃR�s�[���Ė��ߍ��񂾏ꍇ�́Ajacode �̑��̃T�u���[�`��
�̌Ăяo���ɐ旧���� jacode::init() �����s���A�����ŗ��p����ϐ�������������
�K�v������܂��B

### �߂�l

����܂���B

# �����

  Copyright (c) 1992,1993,1994 Kazumasa Utashiro
  Copyright (c) 1995-2000 Kazumasa Utashiro
  Copyright (c) 2002 Kazumasa Utashiro
  Copyright (c) 2010, 2011, 2014, 2015, 2016, 2017, 2018 INABA Hitoshi

# ���쌠

�I���W�i���� "jcode.pl" �Ɠ��������ŗ��p�ł��܂��B�ȉ��Ɉ��p���܂��B

  This software is free software;
  
  Use and redistribution for ANY PURPOSE are granted as long as all
  copyright notices are retained.  Redistribution with modification
  is allowed provided that you make your modified version obviously
  distinguishable from the original one.  THIS SOFTWARE IS PROVIDED
  BY THE AUTHOR ``AS IS'' AND ANY EXPRESS OR IMPLIED WARRANTIES ARE
  DISCLAIMED.
  
  This software is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

