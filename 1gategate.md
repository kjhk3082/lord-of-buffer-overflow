0x8048430 <main>:       push   %ebp
0x8048431 <main+1>:     mov    %ebp,%esp 

0x8048433 <main+3>:     sub    %esp,0x100 // 100바이트 할당

0x8048439 <main+9>:     cmp    DWORD PTR [%ebp+8],1 // [ebp+8]은 첫번째 argument이므로 argc
0x804843d <main+13>:    jg     0x8048456 <main+38>  // if(argc <=1) 

0x804843f <main+15>:    push   0x80484e0
0x8048444 <main+20>:    call   0x8048350 <printf> // printf( "argv error\n");
0x8048449 <main+25>:    add    %esp,4 // 함수리턴

0x804844c <main+28>:    push   0  // 함수의 argument
0x804844e <main+30>:    call   0x8048360 <exit> // exit(0)
0x8048453 <main+35>:    add    %esp,4 // 함수 리턴

0x8048456 <main+38>:    mov    %eax,DWORD PTR [%ebp+12] // [ebp+12]는 두번째 argument이므로 *argv[0]
0x8048459 <main+41>:    add    %eax,4
0x804845c <main+44>:    mov    %edx,DWORD PTR [%eax]  //  argv[1]
0x804845e <main+46>:    push   %edx
0x804845f <main+47>:    lea    %eax,[%ebp-256]  // strcpy의 두번째 argument argv[1]
0x8048465 <main+53>:    push   %eax // strcpy의 첫번재 argument &buffer[0]
0x8048466 <main+54>:    call   0x8048370 <strcpy> // strcpy(buffer,argv[1])
0x804846b <main+59>:    add    %esp,8 // 함수리턴

0x804846e <main+62>:    lea    %eax,[%ebp-256]  // &buffer[0]
0x8048474 <main+68>:    push   %eax // &buffer[0]
0x8048475 <main+69>:    push   0x80484ec  // "%s\n"
0x804847a <main+74>:    call   0x8048350 <printf> // printf(""%s\n",buffer)
0x804847f <main+79>:    add    %esp,8 // 함수리턴

0x8048482 <main+82>:    leave
0x8048483 <main+83>:    ret
