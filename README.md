# Sistem-PD
k1 = 50;
k2 = 90;
a1 = 20;
a2 = 15;
m1 = 20;
m2 = 30;
syms t
X0=[2;3;6;5];

A = [0 1 0 0;-(k1+k2)/m1 -(a1+a2)/m1 k2/m1 a2/m1;0 0 0 1;k2/m2 a2/m2 -k2/m2 -a2/m2];
[V,D]=eig(A); % V = eigenvector, D =eigenvalue
L = diag(D);
C=inv(V)*X0;

Y = C(1)*V(1,1)*exp(L(1)*t) + C(2)*V(1,2)*exp(L(2)*t) + C(3)*V(1,3)*exp(L(3)*t) + C(4)*V(1,4)*exp(L(4)*t)
Z = C(1)*V(3,1)*exp(L(1)*t) + C(2)*V(3,2)*exp(L(2)*t) + C(3)*V(3,3)*exp(L(3)*t) + C(4)*V(3,4)*exp(L(4)*t)

o1 = fplot(Y,[0,75], 'color', 'blue', 'LineWidth', 1.5);
title('2 benda dengan peredam')
xlabel('Waktu(t)')
ylabel('Jarak y(t)')
legend()
hold on
o2 = fplot(Z,[0,75], 'color', 'red', 'LineWidth', 1.5);
x_axis = line(xlim, [0,0], 'color', 'black');
hold off
legend([o1 o2],{'Benda 1', 'Benda 2'}, 'location', 'northeast')
