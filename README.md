Ludidi-Staff
============
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Collections;

namespace Act01
{
    class CheckExpr
    {
        public Stack checkList = new Stack();

        public bool wellFormed(String expr)
        //pre:  expr.Length > 0            
        //post: return true if expr is well-formed, otherwise return false
        {
            for (int x = 0; x <= expr.Length - 1; x++)
            {
                char CurChar = expr[x];
                switch (CurChar)
                {
                    case '{':
                    case '[':
                    case '(': checkList.Push(CurChar);
                        break;
                    case '}': if(checkList.Count!=0){if (checkList.Peek().Equals('{'))
                            checkList.Pop();
                        else return false;}
                        break;
                    case ']': if (checkList.Count != 0)
                        {
                            if (checkList.Peek().Equals('['))
                                checkList.Pop();
                            else return false;
                        }
                        break;
                    case ')': if (checkList.Count != 0)
                        {
                            if (checkList.Peek().Equals('('))
                                checkList.Pop();
                            else return false;
                        }
                        break;
                    default: break;                        
                }
            }

            if (checkList.Count != 0)
            {
                checkList.Clear();
                return false;
            }
            // ADD CODE FOR METHOD wellFormed BELOW


            return true; // remove this statement once your code is done - this is just to ensure that the program compiles

        }
