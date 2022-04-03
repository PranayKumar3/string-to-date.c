#include "stdio.h"
#include "string.h"
#include "stdlib.h"
#include "string_to_date.h"
#include "unity.h"

error_t string_to_date_converter(char* input_string, my_date_t* result_date)
{
    if(input_string==NULL||result_date==NULL)
        return NULL_PTR;
        
	int init_size = strlen(input_string);
	char delimiter[] = "/";

	char *ptr = strtok(input_string, delimiter);
    int num[3], i=-1;
	
    while(ptr != NULL)
	{
        i++;
        num[i]=atoi(ptr);
		ptr = strtok(NULL, delimiter);
        
	}
    
    if(num[0]>0 && num[0]<32 && num[1]>0 && num[1]<13 && num[2]>0)
    {
        result_date->date=num[0];
        result_date->month=num[1];
        result_date->year=num[2];
        return SUCCESS;
    }
    
    else
        return INCORRECT;
}
