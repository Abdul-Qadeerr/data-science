{
  "cells": [
    {
      "cell_type": "markdown",
      "id": "intro",
      "metadata": {},
      "source": [
        "# 📘 Pandas Implementation Examples\n",
        "This notebook covers basic to intermediate concepts of Pandas."
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 1,
      "id": "import",
      "metadata": {},
      "outputs": [],
      "source": [
        "import pandas as pd\n",
        "import numpy as np"
      ]
    },
    {
      "cell_type": "markdown",
      "id": "series",
      "metadata": {},
      "source": [
        "## 1. Creating Series"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 2,
      "id": "series-example",
      "metadata": {},
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Series:\n",
            "0    10\n",
            "1    20\n",
            "2    30\n",
            "3    40\n",
            "dtype: int64\n",
            "\n",
            "Custom Index:\n",
            "A    100\n",
            "B    200\n",
            "C    300\n",
            "dtype: int64\n"
          ]
        }
      ],
      "source": [
        "s1 = pd.Series([10, 20, 30, 40])\n",
        "s2 = pd.Series([100, 200, 300], index=[\"A\", \"B\", \"C\"])\n",
        "\n",
        "print(\"Series:\")\n",
        "print(s1)\n",
        "print(\"\\nCustom Index:\")\n",
        "print(s2)\n"
      ]
    },
    {
      "cell_type": "markdown",
      "id": "dataframe",
      "metadata": {},
      "source": [
        "## 2. Creating DataFrame"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 3,
      "id": "df-example",
      "metadata": {},
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "   Name  Age  Score\n",
            "0  Ali   22     85\n",
            "1  Sara  24     90\n",
            "2  John  21     75\n"
          ]
        }
      ],
      "source": [
        "data = {\"Name\": [\"Ali\", \"Sara\", \"John\"],\n",
        "        \"Age\": [22, 24, 21],\n",
        "        \"Score\": [85, 90, 75]}\n",
        "df = pd.DataFrame(data)\n",
        "print(df)\n"
      ]
    },
    {
      "cell_type": "markdown",
      "id": "selection",
      "metadata": {},
      "source": [
        "## 3. Selection & Indexing"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 4,
      "id": "df-selection",
      "metadata": {},
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Name column:\n",
            "0     Ali\n",
            "1    Sara\n",
            "2    John\n",
            "Name: Name, dtype: object\n",
            "\n",
            "Row 1:\n",
            "Name     Sara\n",
            "Age        24\n",
            "Score      90\n",
            "Name: 1, dtype: object\n"
          ]
        }
      ],
      "source": [
        "print(\"Name column:\")\n",
        "print(df[\"Name\"])\n",
        "print(\"\\nRow 1:\")\n",
        "print(df.loc[1])\n"
      ]
    },
    {
      "cell_type": "markdown",
      "id": "operations",
      "metadata": {},
      "source": [
        "## 4. Basic Operations"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 5,
      "id": "df-operations",
      "metadata": {},
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Mean Age: 22.333333333333332\n",
            "Max Score: 90\n"
          ]
        }
      ],
      "source": [
        "print(\"Mean Age:\", df[\"Age\"].mean())\n",
        "print(\"Max Score:\", df[\"Score\"].max())\n"
      ]
    },
    {
      "cell_type": "markdown",
      "id": "filtering",
      "metadata": {},
      "source": [
        "## 5. Filtering Data"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 6,
      "id": "df-filtering",
      "metadata": {},
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "   Name  Age  Score\n",
            "1  Sara   24     90\n"
          ]
        }
      ],
      "source": [
        "filtered = df[df[\"Score\"] > 80]\n",
        "print(filtered)\n"
      ]
    },
    {
      "cell_type": "markdown",
      "id": "groupby",
      "metadata": {},
      "source": [
        "## 6. GroupBy & Aggregation"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 7,
      "id": "df-groupby",
      "metadata": {},
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "  Dept  Age\n",
            "0    IT   23\n",
            "1   HR   24\n"
          ]
        }
      ],
      "source": [
        "data2 = {\"Name\": [\"Ali\", \"Sara\", \"John\", \"Ayesha\"],\n",
        "         \"Dept\": [\"IT\", \"HR\", \"IT\", \"HR\"],\n",
        "         \"Age\": [22, 24, 21, 24]}\n",
        "df2 = pd.DataFrame(data2)\n",
        "print(df2.groupby(\"Dept\")[\"Age\"].mean().reset_index())\n"
      ]
    },
    {
      "cell_type": "markdown",
      "id": "merge",
      "metadata": {},
      "source": [
        "## 7. Merging & Joining"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 8,
      "id": "df-merge",
      "metadata": {},
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "   ID Name_x Dept Name_y\n",
            "0   1   Ali   IT   Ali\n",
            "1   2   Sara   HR   Sara\n"
          ]
        }
      ],
      "source": [
        "df1 = pd.DataFrame({\"ID\": [1, 2], \"Name\": [\"Ali\", \"Sara\"], \"Dept\": [\"IT\", \"HR\"]})\n",
        "df2 = pd.DataFrame({\"ID\": [1, 2], \"Name\": [\"Ali\", \"Sara\"]})\n",
        "merged = pd.merge(df1, df2, on=\"ID\")\n",
        "print(merged)\n"
      ]
    },
    {
      "cell_type": "markdown",
      "id": "reading",
      "metadata": {},
      "source": [
        "## 8. Reading/Writing CSV"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 9,
      "id": "df-csv",
      "metadata": {},
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "   Name  Age  Score\n",
            "0  Ali   22     85\n",
            "1  Sara  24     90\n",
            "2  John  21     75\n"
          ]
        }
      ],
      "source": [
        "# Saving to CSV\n",
        "df.to_csv(\"students.csv\", index=False)\n",
        "\n",
        "# Reading from CSV\n",
        "df_loaded = pd.read_csv(\"students.csv\")\n",
        "print(df_loaded)\n"
      ]
    }
  ],
  "metadata": {
    "colab": {
      "provenance": []
    },
    "language_info": {
      "name": "python"
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    }
  },
  "nbformat": 4,
  "nbformat_minor": 5
}
