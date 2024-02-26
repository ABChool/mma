import pandas as pd
import os

# CSV 파일이 있는 폴더 경로 지정
folder_path = 'C:\\Users\\시설안전공단\\Desktop\\test'  # 이 경로를 실제 폴더 경로로 수정하세요.

# 폴더 내 모든 파일 순회
for file_name in os.listdir(folder_path):
    # .csv 파일인지 확인
    if file_name.endswith('.csv'):
        # 파일 전체 경로 구성
        file_path = os.path.join(folder_path, file_name)
        
        # CSV 파일 읽기 (첫 6행 제외)
        df = pd.read_csv(file_path, skiprows=6)
        
        # 수정된 데이터프레임을 원본 파일명으로 저장하여 원본 파일 덮어쓰기
        # 또는 'modified_' 접두사를 추가한 새 파일명으로 저장
        new_file_path = os.path.join(folder_path, 'modified_' + file_name)
        df.to_csv(new_file_path, index=False)

        print(f'File processed and saved as: {new_file_path}')

