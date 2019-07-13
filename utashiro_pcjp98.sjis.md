This file was translated to Markdown format from
ftp://ftp.oreilly.co.jp/pcjp98/utashiro/utashiro.mgp
in Shift_JIS encoding.

���̃t�@�C����
ftp://ftp.oreilly.co.jp/pcjp98/utashiro/utashiro.mgp
�� Markdown �L�@�ɂ���ď������������̂ł��B

-----
Perl�ɂ����{�ꏈ��
PerlConference Tokyo '98 1998�N11��11���A����

# Perl �ɂ����{�ꏈ��

### (��)�C���^�[�l�b�g�C�j�V�A�e�B�u
### �̑� �a��
### <utashiro@iij.ad.jp>

### 1998�N11��11��

�uPerlConference Tokyo�v�͌����̂܂܂ł��B

-----
## ���{�ꕶ����̎�舵��

### �v���O�������ł̕\���|���ꕶ���Ƃ̏Փ�

### ���e����

    # EUC �������炠�܂�C�ɂ��Ȃ��Ă���
    print "����� EUC �̃R�[�h�ł��B\n"

    # SJIS �̏ꍇ�͍���̂� here document
    $s = <<'EOT'
    �u�\�v��u�ځv�Ƃ��������ɂ̓o�b�N�X���b�V�����܂܂��
    EOT
    # �Ō�� \n ������̂ŁA�s�v�Ȃ��菜��
    #�u�ځv�͌����̂܂܂ł��B

### �ϐ�
�ϐ��ɑ������ꍇ�͂Ƃ肠�����͋C�ɂ��Ȃ��Ă�����
�ł��g���Ƃ��ɂ͒���

    if (/$s/) {...

-----
## ���{�ꕶ����̎�舵��

### ��ʓI�ȏ����`��

### �����R�[�h�� EUC ���֗�

* ���ꕶ�����܂܂�Ȃ�
* ���������� /[\200-\377]{2}/ �ł��}�b�`�\
* �ł��⏕�����������3�o�C�g�Ȃ̂���...
* JIS X 0201 ������2�o�C�g�����Ǖ\������...
* JIS �� SJIS ����̕ϊ��͔�r�I�e��

### SJIS �ł��A�����̃p�^�[���Ɉˑ����Ȃ������Ȃ�卷�Ȃ�

### �����R�[�h�𗘗p���鏈���̗���

    ���͂�����R�[�h�ɕϊ�
    ��
    ����
    ��
    �O���R�[�h�ɕϊ����ďo��

-----
## ���{�ꕶ����̎�舵��

### �����̎�舵���|���o�C�g�����R�[�h

    # �����̕����̗� (EUC)
    $_ = '���{��Ɖp�� (English) �����݂������B';
    @chars = /[\200-\377].|./g;
    $" = '|';
    print "@chars\n";
    
    ��|�{|��|��|�p|��| |(|E|n|g|l|i|s|h|)| |��|��|��|��|��|��|�B

    # �����Ɛ^�ʖڂɍ���
    $re_euc_c    = '[\241-\376][\241-\376]';     # X0208
    $re_euc_kana = '\216[\241-\337]';            # X0201
    $re_euc_0212 = '\217[\241-\376][\241-\376]'; # X0212 �⏕����
    @chars = /$re_euc_c|$re_euc_kana|$re_euc_0212|./go;
    $" = '|';
    print "@chars\n";

-----
## ���{�ꕶ����̎�舵��

### JIS �R�[�h�̏����̗�|���[�h�̑���

### �G�X�P�[�v�V�[�N�G���X�� split ���Ă��܂��ƕ֗�

    @list = split(/(\e\$B|\e\(B)/);
    for $s (@list) {
        if    ($s eq "\e\$B") {
            $japanese = 1; next;    # ���{��̎n�܂�
        }
        elsif ($s eq "\e\(B") {
            $japanese = 0; next;    # ASCII �̎n�܂�
        }

        # ���{�ꂾ�����璷���̔����AASCII �������璷�����𕶎����Ƃ��Đ�����
        $char_count = $japanese ? length($s) / 2 : length($s);
    }

### �{���� JIS X 0208-1978,1990 ������������������

-----
## ���{�ꕶ����̎�舵��

### �����s�ɓn�镶����̌����|�킩���������

�e�����̊Ԃɉ��s (whitespace) ��G�X�P�[�v�V�[�N�G���X�������u�����v����Ȃ�

### �Q�l: mg �R�}���h�̃f�o�b�O�o�̗͂�

    # EUC
    % mg -dm -j euc '�����񌟍�' /dev/null
    opt_p=/\312\270\s*\273\372\s*\316\363\s*\270\241\s*\272\367/

    # SJIS
    % mg -dm -j sjis '�����񌟍�' /dev/null
    opt_p=/\225\266\s*\216\232\s*\227\361\s*\214\237\s*\215\365/

    # JIS
    % mg -dm -j jis '�����񌟍�' /dev/null
    opt_p=/J8(\e\$\@|\e\$B|\e\(J|\e\(B|\s)*
    \;z(\e\$\@|\e\$B|\e\(J|\e\(B|\s)*
    Ns(\e\$\@|\e\$B|\e\(J|\e\(B|\s)*
    8\!(\e\$\@|\e\$B|\e\(J|\e\(B|\s)*\:w/

-----
## ���{�ꕶ����̎�舵��

### �^�u�̓W�J�|�����񒷂ƕ\�����̈Ⴂ

### �P���ȗ�

    1 while s/\t+/' ' x (length($&) * 8 - length($`) % 8)/e;

### JIS �R�[�h�����������

    # ���{�ꕶ����̕\����̕���Ԃ�
    sub jlength {
        return(length($_[0])) unless $_[0] =~ /\033/;
        local($_) = shift;
        s/\033\$[\@B]|\033\([JB]//g;
        length;
    }
    1 while s/\t+/' ' x (length($&) * 8 - jlength($`) % 8)/e;

-----
## �R�[�h�ϊ�: ���̓t�@�C��

JIS �� SJIS �́A�����R�[�h�Ƃ��Ĉ����ɂ���

EUC �ɕϊ����Ă��珈������ƈ����₷��

    # �W���I�ȃt�@�C������
    open(F, $file) or die;

    # nkf �ŃR�[�h�ϊ�����
    open(F, "nkf -e $file|") or die;

### ���_:
* �t�@�C�������݂��Ȃ��Ă��G���[�ɂȂ�Ȃ�
* �R�}���h���Ȃ��Ă��G���[�ɂȂ�Ȃ�

-----
## �R�[�h�ϊ�: �o�̓t�@�C��

    # �ʏ�̃t�@�C���o��
    open(OUT, ">$outfile") or die "$outfile: $!\n";
    while (<>) {
        print OUT $_;
    }

    # �R�[�h�ϊ������ăt�@�C���ɏo��
    open(OUT, "|nkf -j > $outfile") or die;
    ...

    # �o�̓t�@�C�����I�[�v���ł��邩�ǂ������`�F�b�N����
    open(OUT, ">$outfile") or die "$outfile: $!\n";
    open(OUT, "|nkf -j > $outfile") or die;
    ...

-----
## �R�[�h�ϊ�: �ϐ��̓��e��ϊ�����

    # �o�b�N�N�H�[�g���g��
    $to = `echo $from | nkf -j`;
    # ���_: �V�F���̓��ꕶ�����G�X�P�[�v����K�v������

    # �Öق� fork ���g��
    unless (open(IN, '-|')) {
        if (open(STDOUT, '|nkf -e')) {
            print $from;
        }
        exit;
    }
    $to = <IN>;

    # ��̗�͂���ȕ��ɂ�������
    open(IN, '-|') or (open(STDOUT, '|nkf -e') and print($from), exit);
    # �{���� fork �Ɏ��s�����ꍇ���l������K�v����

-----
## �R�[�h�ϊ�: IPC::Open2 �𗘗p����

    # IPC::Open2 ���W���[�����g��
    use IPC::Open2;
    $from = "�d�t�b������\n";
    $pid = open2(\*IN, \*OUT, 'nkf -j');
    print OUT $from;
    close OUT;
    $to = <IN>;
    close IN;

Perl4 �ł� open2.pl

-----
## �R�[�h�ϊ�: jcode.pl

* Perl (Perl4) �ɂ����{�ꕶ���R�[�h�ϊ����C�u����
* �^�C�v�O���u�ŕ������n��
* Perl5 ������ϐ����t�@�����X�ɂ���ė��p�\

### �|�[�^�r���e�B
* jcode.pl ��������΂ǂ��ł����p�\
* �ŋ߂� jperl �ł͗��p�\ (�炵��)

### ���s���x
* ���ʂ̃f�[�^�ɂ͎��p�I�ȑ��x�����A��͂�x��
* ��ʂ̃f�[�^�ɂ͊O���R�}���h�𗘗p���������L��

-----
## �R�[�h�ϊ�: jcode.pl

### �w�肵���R�[�h�ɕϊ�

    # $string �̓��e�� JIS �ɕϊ������
    # $code �ɂ͌��̃R�[�h���Ԃ�
    require 'jcode.pl';
    $code = jcode::convert(\$string, "jis");

### �Q�Ɠn���̗��R
* �R�[�h�ϊ����K�v�Ȃ����ɂ̓f�[�^���R�s�[�������Ȃ�
* �v���O���~���O�ɏ\���C������Ή���͉\����...

### ���̃R�[�h���������Ă���ꍇ

    $code = jcode::convert(\$string, "jis", "sjis");

### �l�n���ɂ��Ăяo���`��

    # �Q�Ɠn�����g���ɂ����ꍇ������
    $string =~ s/^(Subject|From|To|Cc):.*$/jcode::euc($&)/mg;

-----
## �R�[�h�ϊ�: jcode.pl

    # ���̓R�[�h�̎�������
    # �R�[�h����C���^�t�F�[�X
    $code = jcode::getcode(\$line)

���̓R�[�h���w�肳��Ȃ��ꍇ�ɂ͎������肷��

### ��������̃A���S���Y��
* �e�L�X�g�ɂȂ�����������΃o�C�i��
* �G�X�P�[�v�V�[�N�G���X������� JIS
* EUC �� SJIS �̃p�^�[���ɑ΂��A��葽���}�b�`�������I��
* ���_�������画��s�\
* �ǂ�����Ȃ���� ASCII
* JIS X 0201 ���� (���p����) �͍l������Ȃ�
* �l������� EUC �� SJIS �̔��萸�x���啝�ɉ�����
* �K�v�ȏꍇ�ɂ́A�O���Ŕ��肵�ē��̓R�[�h���w�肷��

-----
## �R�[�h�ϊ�: jcode.pl

JIS X 0201 ���� �� JIS X 0208 ����

�����A�S�p���� �� ���p�����ϊ�

���۔����������l�͑������A���Ɋȕւȕ\�����@���Ȃ�

### jcode::h2z_xxx, jcode::z2h_xxx
* �R�[�h���̕ϊ��֐�
* jcode::convert �̃I�v�V�����Ŏw��
* �������肵�đΉ�����ϊ��֐������s
* ���p���܂܂�Ă���Ǝ�������Ɏ��s����\�����������Ƃɒ���

### jcode::convert(\$line, $ocode [, $icode [, $option]])
* z: X0201 �� X0208 (���p->�S�p)
* h: X0208 �� X0201 (�S�p->���p)

-----
## �R�[�h�ϊ�: jcode.pl

JIS X 0208 �p���� �� ASCII

������ �� �Љ���

tr �֐��̃G�~�����[�V����

�͈͂��w�肷��ꍇ�́A�J�n�����ƏI��������1�o�C�g������ł��邱�Ƃ�����

    jcode::tr('�`-�y��-���O-�X', 'A-Za-z0-9');
    jcode::tr('��-��', '�@-��');

Perl �� tr �֐��̓e�[�u�����Q�Ƃ��ĕϊ�����̂ŋɂ߂č��������Ajcode::tr
�́A�A�z�z����g���� s/../../ �̌`�ɕϊ�����̂ł��Ȃ�x�����Ƃɒ���

-----
