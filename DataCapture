path = 'C:\Users\Administrator\Desktop\Tail_687_1';
fileExt = '*.mat';
files = dir(fullfile(path,fileExt));
len = size(files,1);
p = 1;
for i=1:len
    r=load(['C:\Users\Administrator\Desktop\Tail_687_1\' files(i).name]);
    %%
    ph=r.PH.data;
    label = 1;
    tagg = 0;
    for j=1 : size(ph)
        if ph(j)==6
            tagg=j;  % 可能有的ph文件里面没有6
            break
        end
        if j == length(ph)
            label = 0;
            break
        end
    end
    if label == 0
        continue
    end
    F=fieldnames(r);%得到所有结构体的名字
    [n,m]=size(F);  % 判断一个mat文件有多少结构体
    r_cell = struct2cell(r); % a_cell is a 2-by-10 cell array
    eval(['save C:\Users\Administrator\Desktop\data\' num2str(p) '.mat']);
%      fid = fopen(['C:\Users\Administrator\Desktop\data',num2str(i),'.mat'],'wt');
%      fclose(fid);
  

    %遍历每个变量
    for k= 1:n
        a = r_cell(k,:);
        a = cell2mat(a);
        tag=a.Rate*tagg;
        [n1,~]=size(a.data);
        temptag = n1 - tag + 1;
        temp1 = [];
        temp1(1:temptag, 1) = a.data(tag:n1);
        a.data = [];
        a.data  = temp1;
        eval([ F{k} ' = a']);
        if k == 1
            save(['C:\Users\Administrator\Desktop\data\',num2str(p),'.mat'],[F{k}]);
        else  
            save(['C:\Users\Administrator\Desktop\data\',num2str(p),'.mat'],[F{k}],'-append');
        end
    
    end
    p = p + 1;
end
