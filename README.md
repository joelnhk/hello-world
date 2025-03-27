#include <iostream>
#include <string>
#include <cctype>


std::string SharedLetters(const std::string &x, const std::string y,const std::string *z){
    std::string z2 = *z;
    std::string::size_type size1 = x.size();
    std::string::size_type size2 = y.size();
    std::string::size_type size3 = z2.size();
    std::string::size_type greatest = std::max(size1, std::max(size2, size3));
    std::string final;
    for (std::string::size_type i = 0; i < greatest; i++){
        if (i >= size1){
            if ((i < size2) && (i < size3) && (z2.at(i) == y.at(i))) {
                final += "1,";
            } else{
                final += "0,";
            }
        } else if(i >= size2){
            if ((i < size1) && (i < size3) && (z2.at(i) == x.at(i))) {
                final += "1,";
            } else{
                final += "0,";
            }
        } else if (i >= size3){
            if ((i < size1) && (i < size2) && (y.at(i) == x.at(i))) {
                final += "1,";
            } else{
                final += "0,";
            }
        } else if ((x.at(i) == y.at(i)) || (x.at(i) == z2.at(i))) {
            if ((x.at(i) == y.at(i)) && (x.at(i) == z2.at(i))) {
                final += "3,";
            } else{
                final += "1,";
            }
        } else if((z2.at(i) == y.at(i)) || (z2.at(i) == x.at(i))){
            if ((z2.at(i) == y.at(i)) && (x.at(i) == z2.at(i))) {
                final += "3,";
            } else{
                final += "1,";
            }
        } else final += "0,";
    }
    return final;
}

int main(){
    std::string x;
    std::string y;
    std::string z;

    std::cin>>x >> y>> z;
    std::cout<<SharedLetters(x,y,&z);

}
