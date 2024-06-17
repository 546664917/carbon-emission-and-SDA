# carbon-emission
clc;
clear;
F=readmatrix('path\carbon.xlsx','Sheet','sheet1','Range','p2:p36'); %直接排放矩阵

Z=readmatrix('path\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','c7:ak41'); %中间投入矩阵
X=readmatrix('path\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','ar7:ar41'); %总产出矩阵
H=readmatrix('path\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','al7:al41'); %居民消费矩阵
IM=readmatrix('path\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','c42:ak42'); %进口
EX=readmatrix('path\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','aq7:aq41'); %出口

I=eye(35); %单位矩阵

r=IM'./(X+IM'-EX); %进口系数
d=I-diag(r); %本地系数
A=Z./X'; %直接消耗系数
Ad=d*A; %本地直接消耗系数
Hd=(d*ones(35,1)).*H; %本地家庭消费
E=(F./X); %本地总排放强度
Eind=((E'/(I-Ad))*diag(Hd))'; %本地家庭消费排放足迹（总量）

# SDA
clc;
clear;
%% 数据准备
E07=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','b7:b7'); %07隐含排放矩阵
E08=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','c7:c7'); %07隐含排放矩阵
E09=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','d7:d7'); %07隐含排放矩阵
E10=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','e7:e7'); %07隐含排放矩阵
E11=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','f7:f7'); %07隐含排放矩阵
E12=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','g7:g7'); %07隐含排放矩阵
E13=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','h7:h7'); %07隐含排放矩阵
E14=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','i7:i7'); %07隐含排放矩阵
E15=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','j7:j7'); %07隐含排放矩阵
E16=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','k7:k7'); %07隐含排放矩阵
E17=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','l7:l7'); %07隐含排放矩阵
E18=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','m7:m7'); %07隐含排放矩阵
E19=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','n7:n7'); %07隐含排放矩阵
E20=readmatrix('E:\MATLAB\Malaysian\result.xlsx','Sheet','2','Range','o7:o7'); %07隐含排放矩阵


C07=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','c2:c36'); %07直接排放矩阵
C08=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','d2:d36'); %08直接排放矩阵
C09=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','e2:e36'); %09直接排放矩阵
C10=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','f2:f36');
C11=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','g2:g36');
C12=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','h2:h36');
C13=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','i2:i36');
C14=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','j2:j36');
C15=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','k2:k36');
C16=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','l2:l36');
C17=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','m2:m36');
C18=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','n2:n36');
C19=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','o2:o36');
C20=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','sheet1','Range','p2:p36');

Z07=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.2','Range','c7:ak41'); %中间投入
Z08=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.3','Range','c7:ak41'); 
Z09=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.4','Range','c7:ak41'); 
Z10=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.5','Range','c7:ak41');
Z11=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.6','Range','c7:ak41');
Z12=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.7','Range','c7:ak41');
Z13=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.8','Range','c7:ak41');
Z14=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.9','Range','c7:ak41');
Z15=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.10','Range','c7:ak41');
Z16=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.11','Range','c7:ak41');
Z17=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.12','Range','c7:ak41');
Z18=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.13','Range','c7:ak41');
Z19=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.14','Range','c7:ak41');
Z20=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','c7:ak41');

X07=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.2','Range','ar7:ar41'); %总产出矩阵
X08=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.3','Range','ar7:ar41');
X09=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.4','Range','ar7:ar41');
X10=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.5','Range','ar7:ar41');
X11=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.6','Range','ar7:ar41');
X12=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.7','Range','ar7:ar41');
X13=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.8','Range','ar7:ar41');
X14=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.9','Range','ar7:ar41');
X15=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.10','Range','ar7:ar41');
X16=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.11','Range','ar7:ar41');
X17=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.12','Range','ar7:ar41');
X18=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.13','Range','ar7:ar41');
X19=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.14','Range','ar7:ar41');
X20=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','ar7:ar41');

IM07=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.2','Range','c42:ak42'); %07进口矩阵
IM08=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.3','Range','c42:ak42');
IM09=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.4','Range','c42:ak42');
IM10=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.5','Range','c42:ak42');
IM11=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.6','Range','c42:ak42');
IM12=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.7','Range','c42:ak42');
IM13=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.8','Range','c42:ak42');
IM14=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.9','Range','c42:ak42');
IM15=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.10','Range','c42:ak42');
IM16=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.11','Range','c42:ak42');
IM17=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.12','Range','c42:ak42');
IM18=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.13','Range','c42:ak42');
IM19=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.14','Range','c42:ak42');
IM20=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','c42:ak42');

EX07=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.2','Range','aq7:aq41'); %07出口矩阵
EX08=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.3','Range','aq7:aq41');
EX09=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.4','Range','aq7:aq41');
EX10=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.5','Range','aq7:aq41');
EX11=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.6','Range','aq7:aq41');
EX12=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.7','Range','aq7:aq41');
EX13=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.8','Range','aq7:aq41');
EX14=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.9','Range','aq7:aq41');
EX15=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.10','Range','aq7:aq41');
EX16=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.11','Range','aq7:aq41');
EX17=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.12','Range','aq7:aq41');
EX18=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.13','Range','aq7:aq41');
EX19=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.14','Range','aq7:aq41');
EX20=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','aq7:aq41');

H07=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.2','Range','al7:al41'); %07居民消费矩阵
H08=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.3','Range','al7:al41');
H09=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.4','Range','al7:al41');
H10=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.5','Range','al7:al41');
H11=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.6','Range','al7:al41');
H12=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.7','Range','al7:al41');
H13=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.8','Range','al7:al41');
H14=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.9','Range','al7:al41');
H15=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.10','Range','al7:al41');
H16=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.11','Range','al7:al41');
H17=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.12','Range','al7:al41');
H18=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.13','Range','al7:al41');
H19=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.14','Range','al7:al41');
H20=readmatrix('E:\MATLAB\Malaysian\malaysia-tables-IO.xlsx','Sheet','Table 1.15','Range','al7:al41');

P07=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b2:b2'); %07人口
P08=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b3:b3');
P09=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b4:b4');
P10=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b5:b5');
P11=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b6:b6');
P12=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b7:b7');
P13=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b8:b8');
P14=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b9:b9');
P15=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b10:b10');
P16=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b11:b11');
P17=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b12:b12');
P18=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b13:b13');
P19=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b14:b14');
P20=readmatrix('E:\MATLAB\Malaysian\carbon.xlsx','Sheet','population','Range','b15:b15');


I=eye(35); %单位矩阵
i=[0;0;0;0;0;1;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0];
%% 中间量计算
e07=C07./X07;
e08=C08./X08;
e09=C09./X09;
e10=C10./X10;
e11=C11./X11;
e12=C12./X12;
e13=C13./X13;
e14=C14./X14;
e15=C15./X15;
e16=C16./X16;
e17=C17./X17;
e18=C18./X18;
e19=C19./X19;
e20=C20./X20;

A07=Z07./X07';
A08=Z08./X08';
A09=Z09./X09';
A10=Z10./X10';
A11=Z11./X11';
A12=Z12./X12';
A13=Z13./X13';
A14=Z14./X14';
A15=Z15./X15';
A16=Z16./X16';
A17=Z17./X17';
A18=Z18./X18';
A19=Z19./X19';
A20=Z20./X20';


r07=IM07'./(X07+IM07'-EX07); %07进口系数
r08=IM08'./(X08+IM08'-EX08); %08进口系数
r09=IM09'./(X09+IM09'-EX09);
r10=IM10'./(X10+IM10'-EX10);
r11=IM11'./(X11+IM11'-EX11);
r12=IM12'./(X12+IM12'-EX12);
r13=IM13'./(X13+IM13'-EX13);
r14=IM14'./(X14+IM14'-EX14);
r15=IM15'./(X15+IM15'-EX15);
r16=IM16'./(X16+IM16'-EX16);
r17=IM17'./(X17+IM17'-EX17);
r18=IM18'./(X18+IM18'-EX18);
r19=IM19'./(X19+IM19'-EX19);
r20=IM20'./(X20+IM20'-EX20);

d07=I-diag(r07); %07本地系数
d08=I-diag(r08); %08本地系数
d09=I-diag(r09); 
d10=I-diag(r10); 
d11=I-diag(r11); 
d12=I-diag(r12); 
d13=I-diag(r13); 
d14=I-diag(r14); 
d15=I-diag(r15); 
d16=I-diag(r16); 
d17=I-diag(r17); 
d18=I-diag(r18); 
d19=I-diag(r19); 
d20=I-diag(r20); 

Ad07=d07*A07;
Ad08=d08*A08;
Ad09=d09*A09;
Ad10=d10*A10;
Ad11=d11*A11;
Ad12=d12*A12;
Ad13=d13*A13;
Ad14=d14*A14;
Ad15=d15*A15;
Ad16=d16*A16;
Ad17=d17*A17;
Ad18=d18*A18;
Ad19=d19*A19;
Ad20=d20*A20;

L07=inv(I-Ad07);
L08=inv(I-Ad08);
L09=inv(I-Ad09);
L10=inv(I-Ad10);
L11=inv(I-Ad11);
L12=inv(I-Ad12);
L13=inv(I-Ad13);
L14=inv(I-Ad14);
L15=inv(I-Ad15);
L16=inv(I-Ad16);
L17=inv(I-Ad17);
L18=inv(I-Ad18);
L19=inv(I-Ad19);
L20=inv(I-Ad20);

Hd07=(d07*ones(35,1)).*H07; %07本地家庭消费
Hd08=(d08*ones(35,1)).*H08; %08本地家庭消费
Hd09=(d09*ones(35,1)).*H09;
Hd10=(d10*ones(35,1)).*H10;
Hd11=(d11*ones(35,1)).*H11;
Hd12=(d12*ones(35,1)).*H12;
Hd13=(d13*ones(35,1)).*H13;
Hd14=(d14*ones(35,1)).*H14;
Hd15=(d15*ones(35,1)).*H15;
Hd16=(d16*ones(35,1)).*H16;
Hd17=(d17*ones(35,1)).*H17;
Hd18=(d18*ones(35,1)).*H18;
Hd19=(d19*ones(35,1)).*H19;
Hd20=(d20*ones(35,1)).*H20;

HH07=Hd07(6,:)*i; %07本地家庭消费木材
HH08=Hd08(6,:)*i; %08本地家庭消费木材
HH09=Hd09(6,:)*i;
HH10=Hd10(6,:)*i;
HH11=Hd11(6,:)*i;
HH12=Hd12(6,:)*i;
HH13=Hd13(6,:)*i;
HH14=Hd14(6,:)*i;
HH15=Hd15(6,:)*i;
HH16=Hd16(6,:)*i;
HH17=Hd17(6,:)*i;
HH18=Hd18(6,:)*i;
HH19=Hd19(6,:)*i;
HH20=Hd20(6,:)*i;

h07=(sum(Hd07,"all"))/P07;
h08=(sum(Hd08,"all"))/P08;
h09=(sum(Hd09,"all"))/P09;
h10=(sum(Hd10,"all"))/P10;
h11=(sum(Hd11,"all"))/P11;
h12=(sum(Hd12,"all"))/P12;
h13=(sum(Hd13,"all"))/P13;
h14=(sum(Hd14,"all"))/P14;
h15=(sum(Hd15,"all"))/P15;
h16=(sum(Hd16,"all"))/P16;
h17=(sum(Hd17,"all"))/P17;
h18=(sum(Hd18,"all"))/P18;
h19=(sum(Hd19,"all"))/P19;
h20=(sum(Hd20,"all"))/P20;

R07=((sum(HH07,"all"))/(sum(Hd07,"all")))*i;
R08=((sum(HH08,"all"))/(sum(Hd08,"all")))*i;
R09=((sum(HH09,"all"))/(sum(Hd09,"all")))*i;
R10=((sum(HH10,"all"))/(sum(Hd10,"all")))*i;
R11=((sum(HH11,"all"))/(sum(Hd11,"all")))*i;
R12=((sum(HH12,"all"))/(sum(Hd12,"all")))*i;
R13=((sum(HH13,"all"))/(sum(Hd13,"all")))*i;
R14=((sum(HH14,"all"))/(sum(Hd14,"all")))*i;
R15=((sum(HH15,"all"))/(sum(Hd15,"all")))*i;
R16=((sum(HH16,"all"))/(sum(Hd16,"all")))*i;
R17=((sum(HH17,"all"))/(sum(Hd17,"all")))*i;
R18=((sum(HH18,"all"))/(sum(Hd18,"all")))*i;
R19=((sum(HH19,"all"))/(sum(Hd19,"all")))*i;
R20=((sum(HH20,"all"))/(sum(Hd20,"all")))*i;
%% 07-08
dE1=sum(E08,"all")-sum(E07,"all");
de1=0.5*((e08-e07)'*L07*R07*h07*P07+(e08-e07)'*L08*R08*h08*P08);
dL1=0.5*(e07'*(L08-L07)*R07*h07*P07+e08'*(L08-L07)*R08*h08*P08);
dR1=0.5*(e07'*L07*(R08-R07)*h07*P07+e08'*L08*(R08-R07)*h08*P08);
dh1=0.5*((e07'*L07*R07*(h08-h07)*P07)+(e08'*L08*R08*(h08-h07)*P08));
dP1=0.5*(e07'*L07*R07*h07*(P08-P07)+e08'*L08*R08*h08*(P08-P07));
dE2=de1+dL1+dR1+dh1+dP1;
%% 08-09
dE1=sum(E09,"all")-sum(E08,"all");
de1=0.5*((e09-e08)'*L08*R08*h08*P08+(e09-e08)'*L09*R09*h09*P09);
dL1=0.5*(e08'*(L09-L08)*R08*h08*P08+e09'*(L09-L08)*R09*h09*P09);
dR1=0.5*(e08'*L08*(R09-R08)*h08*P08+e09'*L09*(R09-R08)*h09*P09);
dh1=0.5*((e08'*L08*R08*(h09-h08)*P08)+(e09'*L09*R09*(h09-h08)*P09));
dP1=0.5*(e08'*L08*R08*h08*(P09-P08)+e09'*L09*R09*h09*(P09-P08));
dE2=de1+dL1+dR1+dh1+dP1;
%% 09-10
dE1=sum(E10,"all")-sum(E09,"all");
de1=0.5*((e10-e09)'*L09*R09*h09*P09+(e10-e09)'*L10*R10*h10*P10);
dL1=0.5*(e09'*(L10-L09)*R09*h09*P09+e10'*(L10-L09)*R10*h10*P10);
dR1=0.5*(e09'*L09*(R10-R09)*h09*P09+e10'*L10*(R10-R09)*h10*P10);
dh1=0.5*((e09'*L09*R09*(h10-h09)*P09)+(e10'*L10*R10*(h10-h09)*P10));
dP1=0.5*(e09'*L09*R09*h09*(P10-P09)+e10'*L10*R10*h10*(P10-P09));
dE2=de1+dL1+dR1+dh1+dP1;
%% 10-11
dE1=sum(E11,"all")-sum(E10,"all");
de1=0.5*((e11-e10)'*L10*R10*h10*P10+(e11-e10)'*L11*R11*h11*P11);
dL1=0.5*(e10'*(L11-L10)*R10*h10*P10+e11'*(L11-L10)*R11*h11*P11);
dR1=0.5*(e10'*L10*(R11-R10)*h10*P10+e11'*L11*(R11-R10)*h11*P11);
dh1=0.5*((e10'*L10*R10*(h11-h10)*P10)+(e11'*L11*R11*(h11-h10)*P11));
dP1=0.5*(e10'*L10*R10*h10*(P11-P10)+e11'*L11*R11*h11*(P11-P10));
dE2=de1+dL1+dR1+dh1+dP1;
%% 11-12
dE1=sum(E12,"all")-sum(E11,"all");
de1=0.5*((e12-e11)'*L11*R11*h11*P11+(e12-e11)'*L12*R12*h12*P12);
dL1=0.5*(e11'*(L12-L11)*R11*h11*P11+e12'*(L12-L11)*R12*h12*P12);
dR1=0.5*(e11'*L11*(R12-R11)*h11*P11+e12'*L12*(R12-R11)*h12*P12);
dh1=0.5*((e11'*L11*R11*(h12-h11)*P11)+(e12'*L12*R12*(h12-h11)*P12));
dP1=0.5*(e11'*L11*R11*h11*(P12-P11)+e12'*L12*R12*h12*(P12-P11));
dE2=de1+dL1+dR1+dh1+dP1;
%% 12-13
dE1=sum(E13,"all")-sum(E12,"all");
de1=0.5*((e13-e12)'*L12*R12*h12*P12+(e13-e12)'*L13*R13*h13*P13);
dL1=0.5*(e12'*(L13-L12)*R12*h12*P12+e13'*(L13-L12)*R13*h13*P13);
dR1=0.5*(e12'*L12*(R13-R12)*h12*P12+e13'*L13*(R13-R12)*h13*P13);
dh1=0.5*((e12'*L12*R12*(h13-h12)*P12)+(e13'*L13*R13*(h13-h12)*P13));
dP1=0.5*(e12'*L12*R12*h12*(P13-P12)+e13'*L13*R13*h13*(P13-P12));
dE2=de1+dL1+dR1+dh1+dP1;
%% 13-14
dE1=sum(E14,"all")-sum(E13,"all");
de1=0.5*((e14-e13)'*L13*R13*h13*P13+(e14-e13)'*L14*R14*h14*P14);
dL1=0.5*(e13'*(L14-L13)*R13*h13*P13+e14'*(L14-L13)*R14*h14*P14);
dR1=0.5*(e13'*L13*(R14-R13)*h13*P13+e14'*L14*(R14-R13)*h14*P14);
dh1=0.5*((e13'*L13*R13*(h14-h13)*P13)+(e14'*L14*R14*(h14-h13)*P14));
dP1=0.5*(e13'*L13*R13*h13*(P14-P13)+e14'*L14*R14*h14*(P14-P13));
dE2=de1+dL1+dR1+dh1+dP1;
%% 14-15
dE1=sum(E15,"all")-sum(E14,"all");
de1=0.5*((e15-e14)'*L14*R14*h14*P14+(e15-e14)'*L15*R15*h15*P15);
dL1=0.5*(e14'*(L15-L14)*R14*h14*P14+e15'*(L15-L14)*R15*h15*P15);
dR1=0.5*(e14'*L14*(R15-R14)*h14*P14+e15'*L15*(R15-R14)*h15*P15);
dh1=0.5*((e14'*L14*R14*(h15-h14)*P14)+(e15'*L15*R15*(h15-h14)*P15));
dP1=0.5*(e14'*L14*R14*h14*(P15-P14)+e15'*L15*R15*h15*(P15-P14));
dE2=de1+dL1+dR1+dh1+dP1;
%% 15-16
dE1=sum(E16,"all")-sum(E15,"all");
de1=0.5*((e16-e15)'*L15*R15*h15*P15+(e16-e15)'*L16*R16*h16*P16);
dL1=0.5*(e15'*(L16-L15)*R15*h15*P15+e16'*(L16-L15)*R16*h16*P16);
dR1=0.5*(e15'*L15*(R16-R15)*h15*P15+e16'*L16*(R16-R15)*h16*P16);
dh1=0.5*((e15'*L15*R15*(h16-h15)*P15)+(e16'*L16*R16*(h16-h15)*P16));
dP1=0.5*(e15'*L15*R15*h15*(P16-P15)+e16'*L16*R16*h16*(P16-P15));
dE2=de1+dL1+dR1+dh1+dP1;
%% 16-17
dE1=sum(E17,"all")-sum(E16,"all");
de1=0.5*((e17-e16)'*L16*R16*h16*P16+(e17-e16)'*L17*R17*h17*P17);
dL1=0.5*(e16'*(L17-L16)*R16*h16*P16+e17'*(L17-L16)*R17*h17*P17);
dR1=0.5*(e16'*L16*(R17-R16)*h16*P16+e17'*L17*(R17-R16)*h17*P17);
dh1=0.5*((e16'*L16*R16*(h17-h16)*P16)+(e17'*L17*R17*(h17-h16)*P17));
dP1=0.5*(e16'*L16*R16*h16*(P17-P16)+e17'*L17*R17*h17*(P17-P16));
dE2=de1+dL1+dR1+dh1+dP1;
%% 17-18
dE1=sum(E18,"all")-sum(E17,"all");
de1=0.5*((e18-e17)'*L17*R17*h17*P17+(e18-e17)'*L18*R18*h18*P18);
dL1=0.5*(e17'*(L18-L17)*R17*h17*P17+e18'*(L18-L17)*R18*h18*P18);
dR1=0.5*(e17'*L17*(R18-R17)*h17*P17+e18'*L18*(R18-R17)*h18*P18);
dh1=0.5*((e17'*L17*R17*(h18-h17)*P17)+(e18'*L18*R18*(h18-h17)*P18));
dP1=0.5*(e17'*L17*R17*h17*(P18-P17)+e18'*L18*R18*h18*(P18-P17));
dE2=de1+dL1+dR1+dh1+dP1;
%% 18-19
dE1=sum(E19,"all")-sum(E18,"all");
de1=0.5*((e19-e18)'*L18*R18*h18*P18+(e19-e18)'*L19*R19*h19*P19);
dL1=0.5*(e18'*(L19-L18)*R18*h18*P18+e19'*(L19-L18)*R19*h19*P19);
dR1=0.5*(e18'*L18*(R19-R18)*h18*P18+e19'*L19*(R19-R18)*h19*P19);
dh1=0.5*((e18'*L18*R18*(h19-h18)*P18)+(e19'*L19*R19*(h19-h18)*P19));
dP1=0.5*(e18'*L18*R18*h18*(P19-P18)+e19'*L19*R19*h19*(P19-P18));
dE2=de1+dL1+dR1+dh1+dP1;
%% 19-20
dE1=sum(E20,"all")-sum(E19,"all");
de1=0.5*((e20-e19)'*L19*R19*h19*P19+(e20-e19)'*L20*R20*h20*P20);
dL1=0.5*(e19'*(L20-L19)*R19*h19*P19+e20'*(L20-L19)*R20*h20*P20);
dR1=0.5*(e19'*L19*(R20-R19)*h19*P19+e20'*L20*(R20-R19)*h20*P20);
dh1=0.5*((e19'*L19*R19*(h20-h19)*P19)+(e20'*L20*R20*(h20-h19)*P20));
dP1=0.5*(e19'*L19*R19*h19*(P20-P19)+e20'*L20*R20*h20*(P20-P19));
dE2=de1+dL1+dR1+dh1+dP1;
